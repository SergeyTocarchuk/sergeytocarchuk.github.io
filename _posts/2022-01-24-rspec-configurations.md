---
layout: post
title: "RSpec Rails Setup"
author: "Serhii T."
categories: journal
tags: [testing,rspec]
image: 
---

- Add RSpec and other useful gems to your Gemfile, and install with Bundler

```
my_app/Gemfile
group :development, :test do
  gem 'rspec-rails'
  gem 'factory_bot_rails'
  gem 'rails-controller-testing'
end
group :test do
  gem 'faker'
  gem 'capybara'
  gem 'guard-rspec'
  gem 'launchy'
end
```

- Set up a test database, if you are using postgresql: you must run _rails db:create_ on the command line to create your development and test databases.

- Configure RSpec:
Run _rails g rspec:install_.
To tweak the default RSpec configuration so that it will format its output in a readable way. To do this, make your .rspec configuration file look like this:

```
--color
--require spec_helper
--format documentation
```

- Configure the Rails Application to generate test files automatically as features are added
Open config/application.rb and add the following code inside the Application class:

```
my_app/config/application.rb
config.generators do |g|
  g.test_framework :rspec,
    :fixtures => false,
    :view_specs => false,
    :helper_specs => false,
    :routing_specs => false,
    :controller_specs => true,
    :request_specs => false
end
```

- g.test_framework :rspec tells Rails to use RSpec for testing.
- :fixtures => false means Rails should not generate fixtures for each model. (Fixtures are the default Rails way of creating sample data for tests.)
- xxxxx_specs => false means that we won't auto-generate spec files for views, helpers, routes, or requests. To start with, we will focus on testing our models, controllers and the user interface/API (feature specs). You may want to change these settings and use tests for the other components, too.

#### Creating the spec files
If you've already run _rails generate rspec:install_, then Rails will automatically make spec files for you when you generate a model. Otherwise, run _rails generate rspec:model #{modelName}_.

To run the model tests file-by-file, run rspec spec/models/{modelName}_spec.rb.

#### Resources:
- [RSpec Homepage](http://rspec.info/)
- [Documentation](https://relishapp.com/rspec/rspec-rails/v/5-0/docs/gettingstarted)