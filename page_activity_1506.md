---
layout: page
title:  "June 2015 Activity Log"
permalink: /activity/2015/june/
---

#### Todo

####Thursday June 11th
* Completed Ruby Koans
* Started Eloquent Javascript 

####Wenesday June 10th
* First half of Ruby Koans
* Revisiting Rails Tutorial by Michael Hartl

####Tuesday June 9th
* Added tidy dummy content to site
* Fixed issue with tags that are more than one word.
* Create seed file with content
* Setup on Heroku
	* Port Development envt to PostgresSql (install & debug postgres on mac)
* <del>Create task to reset database every 5 minutes so I can give logins</del>
	* 	Couldn't do this on free Heroku unfortunately. Learned a lot trying though.
*  Finished SimpleCMS project, at least for now.


####Monday June 8th
* Completed interface to add & remove tags from posts form
* JS for ajax tag removal called from post form
* add random color to newly created tag. tidy tag controller
* route & action to delete tagging
* markup & styling for 'remove tag' control in post form
* added route/control to regenerate tag related css
* added class method for generating tag css. also added pre_validation callback.
* Styles for tags & tag pages
* Completed module to generate tag css from db >> file

####Sunday June 7th

####Saturday June 6th

####Friday June 5th
* created tag model and taggings model for posts & tags
* moved styling for tags to shared & added dynamic styling per tag
* added posts/tag/:tagname route
* added views & controls for post tags
* manage tags page w/ ajax edit & delete capabilities
* Lots of learning around how Rails works with Ajax & jQuery Ujs





####Thursday June 4th
* Completed Settings
* Add pagination to index views
* Admins - Validate admin password == password_conf
* protect settings & menus from non superadmin
* redirect /cms to sign_in if not signed in
* add current_admin password cofirmation to superadmin actions

####Wednesday June 3rd
* Setup Settings Page
	* Created Admin UI for settings
	* Integrated settings to front end 
* Setup menu settings under settings controller
	* Created Admin page for managing menus  

####Tuesday June 2nd
* Setup Superadmin
	* Add superadmin capability
	* Protect superadmin content
	* Give admins ability to manage their profiles 
* Improve Admin Ui
	* 	Added navbar
	*  added menu icons
	*  added controls for responsive usage
* Swapped out editor for markdown editor
* Added posts resource type
* Fix issue with no page onload due to turbo links


####Monday June 1st
* Setup admin management
	* cms/admins controllers & routes
	* views, forms & links 	

[&larr; Back to all activity](/activity/)