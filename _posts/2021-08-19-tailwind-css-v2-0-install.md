---
layout: post
title: "How to install Tailwind CSS v2.0 using Ruby on Rails"
author: "Serhii T."
categories: journal
tags: [css,tailwind,rails]
image: tailwind_logo.png
---

### Install Tailwind via npm

Install Tailwind and its peer-dependencies by running command:

```
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

Create your configuration file: with the node modules installed we can generate a new _tailwind.config.js_ file. 

```
npx tailwindcss init
```
That will create a new _tailwind.config.js_ file at the root of your Ruby on Rails project.

That file can remain there but I like to move it into where we will be working more with our styles that Tailwind CSS brings us.

Inside _app/javascript/_ I'll create a new folder called _stylesheets_ and move the configuration file there.

Additionally I'll create a new _application.scss_ stylesheet within _app/javascript/stylesheets_.

Our folder structure should resemble the following:

```
app/
  javascript/
    packs
    stylesheets/
    - application.scss
    - tailwind.config.js
```

### Include Tailwind CSS

Inside the _application.scss_ we just create we will need to add these import statements for Tailwind to includes all of its defaults:
```
/* app/javascript/stylesheets/application.scss */
@import "tailwindcss/base";
@import "tailwindcss/components";

/* Add any custom CSS here */
@import "tailwindcss/utilities";
```

You can add any custom CSS after the **components** import but before the **utilities** import.

### Import the stylesheet inside your packs file of choice

Ruby on Rails ships with an _application.js_ file inside _app/javascript/packs_. You can add another file or import it inside _application.js_ all the same. We'll need to import the _application.scss_ file here and leverage Webpack loaders to compile things down:

```
/* app/javascript/packs/application.js */

import Rails from "@rails/ujs"
import Turbolinks from "turbolinks"
import * as ActiveStorage from "@rails/activestorage"
import "channels"

import "stylesheets/application" // Add this line
```

### Require Tailwind CSS inside _postcss.config.js_

To add TailwindCSS to the Ruby on Rails project's _postcss.config.js_ file you need to require it. You can then pass the relative path to your configuration file. Because I added our configuration in the folders within _app/javascript_ I needed to pass the full relative URL _app/javascript/stylesheets/tailwind.config.js_ to make this work:

```
/* postcss.config.js */
module.exports = {
  plugins: [
    require("tailwindcss")("./app/javascript/stylesheets/tailwind.config.js"),
    require("postcss-import"),
    require("postcss-flexbugs-fixes"),
    require("postcss-preset-env")({
      autoprefixer: {
        flexbox: "no-2009",
      },
      stage: 3,
    }),
  ],
}
```

### Update your layout file

New Ruby on Rails projects doesn't assume you'll need to account for stylesheets in your _app/javascript_ folder. As a result, we need to add a stylesheet_pack_tag to our project:

```
<%= stylesheet_pack_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>
```
The stylesheet_pack_tag refers to the _application.scss_ file we created and imported into the _application.js_ file inside _app/javascript/packs_. Styles will be injected dynamically thanks to the default Webpack and PostCSS configuration that now comes by default in Rails 6 applications.

### Make sure you purge those files

Once you have Tailwind CSS up and running I highly recommend setting up the **purge feature** which is now built-in. Simply pass in the paths to files you use Tailwind CSS inside. The utility will traverse those files and remove any classes you aren't making use of.

This reduces file sizes and increases your website's performance dramatically.

```
/* app/javascript/stylesheets/tailwind.config.js */
module.exports = {
  purge: [
    "./app/**/*.html.erb",
    "./app/helpers/**/*.rb",
    "./app/javascript/**/*.js",
    "./app/javascript/**/*.vue",
  ],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```
### Resources

- installation guide at [TailwindCSS documentation](https://tailwindcss.com/docs/installation).