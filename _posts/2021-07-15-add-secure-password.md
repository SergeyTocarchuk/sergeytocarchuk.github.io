---
layout: post
title: "Add Secure Password to your Ruby on Rails application"
author: "Serhii T."
categories: journal
tags: [password, rails]
image: secure_password.jpg
---

3 step process to add auth system functionality from the back-end.

### Step 1. Add bcrypt gem:

In the Gemfile uncomment the line that lists the gem:

```
gem 'bcrypt', '~> 3.1.7'
```
To install the gem in your app run:

```
$ bundle install
```

### Step 2. Add has_secure_password 

To your model file add the line below:

```
has_secure_password
```

### Step 3. Add the password_digest column to your table.

Create a migration file to add the password_digest column to the your table.

```
$ rails generate migration add_password_digest_to_modelname
```

Then pull up the migration file and fill in the column details within the def change method:

```
add_column :modelname, :password_digest, :string
```
Save the file and to make the change to the table run:
```
$ rails db:migrate 
```

And that’s it!