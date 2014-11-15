---
layout: post
title: Blank Rails Assets on Heroku
time: '20:50:03'
day: 10
month: April
year: 2013
---

Working through the Ruby on Rails Tutorial for Rails 4.0 and pushing to heroku
after adding the bootstrap css and assets the css files were coming up blank.

Changing `config.assets.compile` to true in  config/environments/production.rb
seemed to fix the issue but I didn't want to leave it configured this way.

Reverting this change and pushing to Heroku brought the behavior back. Running
`heroku run rake assets:precompile` seems to fix the issue.

**UPDATE:** Seems this is only a temporary fix. According to
[this](http://stackoverflow.com/questions/15354539/heroku-does-not-compile-files-under-assets-piplines-in-rails-4)
post it's an issue with Heroku's support of Rails 4. 
