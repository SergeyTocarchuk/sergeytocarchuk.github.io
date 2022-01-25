---
layout: post
title: "Useful Gems for Testing: Shoulda Matchers"
author: "Serhii T."
categories: journal
tags: [testing,gems,shoulda-matchers]
image: 
---

[Shoulda Matchers](https://github.com/thoughtbot/shoulda-matchers#rails-apps) allows you to write one-line code to test common Rails functionality. For prompt setup of gem add it to _Gemfile_ and run _bundle install_.

Then place this at the bottom of spec/rails_helper.rb:

```
Shoulda::Matchers.configure do |config|
  config.integrate do |with|
    with.test_framework :rspec
    with.library :rails
  end
end
```