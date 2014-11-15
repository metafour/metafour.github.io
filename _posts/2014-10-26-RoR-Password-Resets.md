---
layout: post
title: Ruby on Rails - Password Resets
time: '14:20:00'
day: 26
month: October
year: 2014
---

In order to learn Ruby on Rails I've been working through the 3rd edition of the [Ruby on Rails tutorial](http://railstutorial.org). Upon reaching the second part of Chapter 9, Account Activation and Password Reset, I decided to implement the feature on my own to test and improve my understanding of Rails.

1. User clicks 'Forgot password' link on Sign in page `<%= link_to 'Forgot password', new_password_reset_path %>`
2. GET request sent to new_password_reset_path ⟶ password_resets/new ⟶ password_resets#new
3. User enters email address in text field and clicks button
4. POST request sent to password_resets_path ⟶ password_resets/ ⟶ password_resets#create
5. User gets email with reset token and email address in link
6. User clicks link in email
7. GET request sent to edit_password_reset_url ⟶ password_resets/:id/edit ⟶ password_resets#edit
8. User enters new password and confirmation
9. PATCH request sent to password_reset_path ⟶ password_resets/:id ⟶ password_resets#update
10. If password and confirmation do not match user is redirected back to the root_url. This is a limitation of the `if` statement in password_resets#update

## Differences

### `session[:email]` vs. `hidden_field_tag :email, @user.email`
- Allows for repeated use of `params[:email]` 

Refactor:


    @user = User.find_by(:email, params[:email])
    @user && @user.authenticated?(:reset, params[:reset_token])


into a `private get_user` method and use a `before_action` callback for `edit` and `update` actions in the `password_resets` controller.

### `update_attribute` vs.`user_params` and `update_attributes`
- Should this method always be used?
- Do we use it when a user updates their info?
- When is it not used? Only during token creation and subsequent digest updates to the db?

### Notifies submitter if an email address isn't on file

If an invalid submission is submitted then the submitter is notified that the address isn't on file. This would actually allow someone to determine if a particular user has an account with the service instead of silently doing nothing. As a result I've modified the `create` action in PasswordResetsController to always display the `flash[:info]` message of `Password reset email sent.` but only send the email and set a token if the user exists in the database already.


### Doesn't cover edge case of when logged in and trying to change password

{% highlight ruby %}
PasswordResetsController
...
def create
  if logged_in?
    redirect_to edit_user_path(current_user)
  else
    render 'new'
  end
end
...
{% endhighlight %}

### Doesn't remove reset_digest and reset_sent_at after successful password reset

Add

    @user.update_columns(reset_digest: nil,reset_sent_at: nil)

to `update` action in PasswordResetsController after a successful update.
