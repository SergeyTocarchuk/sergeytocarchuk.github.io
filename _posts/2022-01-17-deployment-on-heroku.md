---
layout: post
title: "Deployment my App on Heroku and What I Learned in Process"
author: "Serhii T."
categories: journal
tags: [heroku,logs]
image: 
---

### Get Started

Sign-up for a [Heroku account](https://www.heroku.com/).

1. Preparation for production deployment:

- Remove _sqlite3 gem_ from top of your Gemfile and paste it to within group _:development, :test do_ block:
```
group :development, :test do
  gem "sqlite3", "~> 1.4"
end
```

- Create a group production with _pg gem_:
```
group :production do
  gem 'pg'
end
```

- Run _bundle install_ to update Gemfile.lock file

2. Check if you already have Heroku CLI installed by going to your terminal by running _heroku --version_

Follow instructions from [Heroku documentation](https://devcenter.heroku.com/articles/getting-started-with-rails6) to install Heroku CLI for Ruby on Rails.

- once installed, login to your Heroku account from your application directory:
```
heroku login
```

- to create a new production version of your app hosted in Heroku, use the following command:
```
heroku create
```

- push your application code to Heroku and deploy your app, use the command below, but make sure all your code changes are committed:
```
git push heroku master
```

- migrate your database:
```
heroku run rake db:migrate
```

- we can now visit the app in our browser with _heroku open_

- if you run into any problems getting your app to perform properly, you will need to check the logs:
```
heroku logs
OR
heroku logs --tail
```

Some tips:
- if you'd like to change the name of your application run:
```
heroku rename newNameOfApp
```

After deployment of my App on Heroku I got an error reference to image_tag
```
ActionView::Template::Error (The asset is not present in the asset pipeline.)
```

I found on [Stackoverflow](https://stackoverflow.com/questions/62977092/actionviewtemplateerror-the-asset-is-not-present-in-the-asset-pipeline-in) that url of image has to be indicated with extension ('ava.jpeg'). It doesn't work for me, and I change configuration in production.rb in config/environments folder to:
```
config.assets.compile = true
```

It's not a good idea, but it works for me know. Have to dive deeper in this later.