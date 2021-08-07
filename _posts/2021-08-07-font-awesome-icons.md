---
layout: post
title: "Add Font Awesome icons to your Ruby on Rails app"
author: "Serhii T."
categories: journal
tags: [documentation,sample]
image: font-awesome-icons.png
---

### Get Started

To add vector icons and social logos on your website with Font Awesome, the web's most popular icon set and toolkit, I downloaded files from [Font Awesome](https://fontawesome.com/v5.15/how-to-use/on-the-web/setup/hosting-font-awesome-yourself): click on _Download Font Awesome Free for the Web_.

From unzipped file copy _all.css_ under css folder and paste it to the project in app/assets/stylesheets folder (rename file if you'd like to).
Also add folder _webfonts_ from archive to the project in app/assets folder.

To the file _application.html.erb_ under folder app/views/layouts add the following line in the head tag under your application style link tag. 

```
<%= stylesheet_link_tag 'name_of_your_file(for example: all)' %>
```

To have a possibility to style your icons open _all.css_ file and add pseudo class ::before to following classes:

```
.fab::before {
  ...
}

.far::before {
  ...
}

.fa::before,
.fas::before {
  ... 
}
```

Now you can add icons to your project:
```
<!-- Google icon -->
<a href="#">
  <i class="fab fa-google"></i>
</a>
```