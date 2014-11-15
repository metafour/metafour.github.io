---
layout: post
title: Capybara Feature Specs
time: '21:36:12'
day: 30
month: March
year: 2013
---

The [Ruby on Rails Tutorial](http://railstutorial.org) now has a beta version addressing the necessary changes in Rails 4. One of these changes is the use of Capybara 2.1.0.beta1 which now uses *feature specs* instead of *request specs*. The current version of the book still uses *request specs* so I'm going to detail the changes I made to use the new *feature specs* in Capybara.

The current version of Chapter 3 lists the following for `spec/requests/static_pages_spec.rb`:
{% highlight ruby %}
    require 'spec_helper'

    describe "Static pages" do

      describe "Home page" do

        it "should have the content 'Sample App'" do
          visit '/static_pages/home'
          expect(page).to have_content('Sample App')
        end

        it "should have the title 'Home'" do
          visit '/static_pages/home'
          expect(page).to have_title("Ruby on Rails Tutorial Sample App | Home")
        end
      end

      describe "Help page" do

        it "should have the content 'Help'" do
          visit '/static_pages/help'
          expect(page).to have_content('Help')
        end

        it "should have the title 'Help'" do
          visit '/static_pages/help'
          expect(page).to have_title("Ruby on Rails Tutorial Sample App | Help")
        end
      end

      describe "About page" do

        it "should have the content 'About Us'" do
          visit '/static_pages/about'
          expect(page).to have_content('About Us')
        end

        it "should have the title 'About Us'" do
          visit '/static_pages/about'
          expect(page).to have_title("Ruby on Rails Tutorial Sample App | About Us")
        end
      end
    end
{% endhighlight %}

Once we complete exercise #2 at the end of the chapter we can update the spec to use the new syntax of *feature specs* like so:

{% highlight ruby %}
    require 'spec_helper'

    feature "static pages" do

      given(:base_title) { "Ruby on Rails Tutorial Sample App" }

      describe "Home page" do

        scenario "should have the content 'Sample App'" do
          visit '/static_pages/home'
          expect(page).to have_content('Sample App')
        end

        scenario "should have the right title" do
          visit '/static_pages/home'
          expect(page).to have_title("#{base_title}")
        end

      end

      describe "Help page" do

        scenario "should have the content 'Help'" do
          visit '/static_pages/help'
          expect(page).to have_content("Help")
        end

        scenario "should have the right title" do
          visit '/static_pages/help'
          expect(page).to have_title("#{base_title} | Help")
        end

      end

      describe "About page" do

        scenario "should have the content 'About'" do
          visit '/static_pages/about'
          expect(page).to have_content("About")
        end

        scenario "should have the right title" do
          visit '/static_pages/about'
          expect(page).to have_title("#{base_title} | About")
        end

      end

      describe "Contact page" do

        scenario "should have the content 'Contact'" do
          visit '/static_pages/contact'
          expect(page).to have_content("Contact")
        end

        scenario "should have the right title" do
          visit '/static_pages/contact'
          expect(page).to have_title("#{base_title} | Contact")
        end

      end
    end
{% endhighlight %}

Unfortunately this still uses the `describe` keyword from the *request specs* DSL due to not wanting to repeat the use of `given` for each `scenario`.