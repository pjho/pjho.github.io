---
layout: post
title:  "SimpleCms - Ruby on Rails Project"
date: 2015-06-08 09:05:10
tags: project rails ruby
---

A simple cms built for the purpose of learning Ruby on Rails. Wanna check it out?

###Demo
[Sign in here](https://frozen-bastion-6147.herokuapp.com/cms) with the details `superadmin@pho.sx` / `password`. Feel free to make changes.

### Source Code
Source code is [available on Github](https://github.com/pjho/rails_simple_cms).

---

##What's Inside?

* Page management & Post Management with spiffy support for markdown editing & live preview.
* Post tags powered with ajaxy goodness
* Basic menu management & easily configurable settings
* Admin management with basic privileges for Superadmins
* All bundled in a slick, bootstrap powered, responsive interface



<div  id="gallery" class="50% row uniform">

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/01_welcome.png">
      <img alt="Welcome" src="/images/thumbs/01_welcome.png">
    </a>
  </div>

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/02_pages.png">
      <img alt="Pages" src="/images/thumbs/02_pages.png">
    </a>
  </div>

  <div class="4u$">
    <a class="image fit thumb" href="/images/fulls/03_posts.png">
      <img alt="Posts" src="/images/thumbs/03_posts.png">
    </a>
  </div>

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/04_post_edit.png">
      <img alt="Post Edit" src="/images/thumbs/04_post_edit.png">
    </a>
  </div>

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/05_tags.png">
      <img alt="Tags" src="/images/thumbs/05_tags.png">
    </a>
  </div>

  <div class="4u$">
    <a class="image fit thumb" href="/images/fulls/06_menus.png">
      <img alt="Menus" src="/images/thumbs/06_menus.png">
    </a>
  </div>

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/07_admins.png">
      <img alt="Admins" src="/images/thumbs/07_admins.png">
    </a>
  </div>

  <div class="4u">
    <a class="image fit thumb" href="/images/fulls/08_settings.png">
      <img alt="Settings" src="/images/thumbs/08_settings.png">
    </a>
  </div>

  <div class="4u$">
    <a class="image fit thumb" href="/images/fulls/09_profile.png">
      <img alt="Profile" src="/images/thumbs/09_profile.png">
    </a>
  </div>

</div>

---
##What did I learn?
Heaps.

Some of the things I feel I really understand about rails after completing this project include:

* Routing, Resorces, Namespacing
* Ajax & Javascript in a rails environment
* Rails' Asset pipeline
* Templating
* HAML
* Validations
* Associations
* Debugging
* Responding, Rendering, Redirecting
* Using external Modules/Classes
* Rails CLI / Server / Console

---

##What would I do differently now?

* Testing!. Having built this I really appreciate the potential value of writing automated tests to make sure changes & refactoring don't break code
* DRY up my code. There's a bit of repetition that I don't love, particularly between posts & pages, that could be abstracted or put into a parent class and extended.
* Settings & Menus have the same model/controller but different ui. I think I would seperate them if I did it again.
* Use a Gem for pretty page/post slugs.
* There's plenty of things I'd add if this was going to be something I was planning to use commercially. For now though, I've learnt a lot and want to get on to the next projects.

---

##Gems Used

* **haml** - HAML syntax for templating
* **bootstrap-sass** - Bootstrap for easy styling
* **pagedown-bootstrap-rails** - Pagedown MarkDown editor
* **redcarpet** - Markdown Renderer
* **rails-settings-cached** - Settings Management Module
* **will_paginate** - Pagination Module
* **will_paginate-bootstrap** - Pagination integration with BootStrap
* **devise** - Authentication
* **exception_handler** - Exception handler gem for custom 404/5** error pages
* **html2haml** - *Development* - Gem to automatically generate Haml from Html/Erb
* **pry-rails** - *Development* - Cleaner console



## Resources Used
Probably a few more than this but these were bookmarked...

#####Associations

* [Tagging from Scratch in Rails](http://www.sitepoint.com/tagging-scratch-rails/)

#####Routes

* [Scoping Rails Routes](http://notahat.com/2014/02/05/scoping-rails-routes.html)
* [Using Rails Namespaces for Admin Actions](http://blog.roberteshleman.com/2014/08/14/using-rails-namespaces-for-admin-actions/)
* [Rails Routing from the Outside In](http://edgeguides.rubyonrails.org/routing.html)

#####Settings

* [Settings Gem](https://github.com/huacnlee/rails-settings-cached)

#####Custom Errors

* [Redirecting to Custom 404 and 500 Pages in Rails](http://easyactiverecord.com/blog/2014/08/19/redirecting-to-custom-404-and-500-pages-in-rails/)

#####Forms

* [Form Helpers - Rails Guides](http://guides.rubyonrails.org/form_helpers.html)

#####Validations

* [Active Record Validations](http://guides.rubyonrails.org/active_record_validations.html)

#####Migrations

* [http://guides.rubyonrails.org/active_record_validations.html](http://edgeguides.rubyonrails.org/active_record_migrations.html)
* [Rails Migration Cheat Sheet](https://gist.github.com/pjho/af5245d59ed0d27d9a6e)

#####Asset Pipeline

* [The Asset Pipeline](http://guides.rubyonrails.org/asset_pipeline.html)

#####Slug / Url

* [Custom Slugs in Rails Without Gems](http://code-worrier.com/blog/custom-slugs-in-rails/)

#####Exceptions
[Ruby Exceptions](http://rubylearning.com/satishtalim/ruby_exceptions.html)
