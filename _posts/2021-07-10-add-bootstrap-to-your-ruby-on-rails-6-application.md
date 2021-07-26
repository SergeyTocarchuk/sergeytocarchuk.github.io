---
layout: post
title: "Add Bootstrap to your Ruby on Rails 6 application"
author: "Serhii T."
categories: journal
tags: [bootstrap, rails]
image: bootsrap_setup.jpg
---

## Use yarn to add Bootstrap and its dependencies - __jquery and popper.js__

Run the following command from your application directory (if you don't have yarn, install it):

yarn add bootstrap@4.3.1 jquery popper.js

You can check that the libraries have been installed properly by checking the package.json file (listed under the Gemfile.lock file in your file directory)
```ruby
    ...
    "bootstrap": "4.4.1",
    "jquery": "^3.6.0",
    "popper.js": "^1.16.1",
    ...
```

## Now for JavaScript

Make the config/webpack/environment.js file look like below:

{% highlight js %}
  const webpack = require("webpack")
  
  environment.plugins.append("Provide", new webpack.ProvidePlugin({
    $: 'jquery',
    jQuery: 'jquery',
    Popper: ['popper.js', 'default']
  }))

  module.exports = environment
{% endhighlight %}

This is so your application's javascript understands jquery and popper.js syntax.
Now you have to import bootstrap and it's goodies to your application.js, go to app/javascript/packs/application.js and add the following line to the bottom:
```
import "bootstrap"
```
That's it for javascript.

## Now onto CSS

Go to app/assets/stylesheets/application.css and add the following line above the require_tree and require_self lines:
```
*= require bootstrap
```
So it looks like below:
```
*= require bootstrap
*= require_tree .
*= require_self
```

Now to add custom styles to the app styling, create a new file within this folder (app/assets/stylesheets folder) and call it custom.css.scss (app/assets/stylesheets/custom.css.scss). Here import the bootstrap library first so you are able to modify styles for not just your new classes but existing bootstrap classes as well:
```
@import 'bootstrap/dist/css/bootstrap';
```

And that's it! you should be good to go with bootstrap 4 in your Rails 6 application.