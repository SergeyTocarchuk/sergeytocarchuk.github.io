---
layout: post
title: "Ruby on Rails: install and setup"
author: "Serhii T."
categories: journal
tags: [rails,foundations]
image:
---

### Install Ruby on Rails

Find the version of [Rails](https://guides.rubyonrails.org/) and run the command:
```
gem install rails -v 6.1.4 // or any other version you prefer
```

To check all installed on you computer versions:
```
gem list rails
```

If you'd like to start new app with specified version of rails:
```
rails _your rails version_ new app_name
```

some useful flags while you start a new app:
```
rails new app_name -d postgresql -B
where
-d postgresql \\ specify a database for a project
-B \\ skip command Bundle install
```