---
layout: post
title: "Namespacing Concept for Routes"
author: "Serhii T."
categories: journal
tags: [rails, routes, namespace]
image: 
---

I'm trying to figure out how to have an index view of List model for users and admins. I want to render all results for an admin and only related Lists for a user. In this case I try to use concept of namespacing: basically it allows us to separate our controllers into different Modules. 

I will group controllers for Admin in my [Todo App](https://github.com/SergeyTocarchuk/todo-list-rails-7).

- create a new folder Admins under _app/controllers_ folder. Here we will collect all controllers related to Admin model.
- start to adding namespacing:
1. create a new file base_controller.rb in _app/controllers/admins_ folder and leave it empty:
```
class Admins::BaseController < ApplicationController

end
```

2. add to class name of every controller **Admins::** and let them inherit from our base_controller.rb:
```
class Admins::AdminsController < Admins::BaseController
```

Now extra level of controller is created and we will change our routes.rb:
```
  namespace :admins do
    resources :admins, only: [:show]
    resources :lists
    resources :users
  end
```

3. In view folder create _admins_ folder and paste there all related to Admin controllers templates. We also need to clean up all url in views.

Now I have separate controllers for admin and url like admins/users or admins/lists.

Resources:
- [Rails guides](https://guides.rubyonrails.org/routing.html#controller-namespaces-and-routing)
- [Rails: Namespacing our Controllers Part 1](https://www.youtube.com/watch?v=1B0Vioz4Ukw)