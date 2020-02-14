# README

<------------     CKEditor     ------------>

1. gem 'jquery-rails' should be added in Gemfile.

2. Add gem 'ckeditor', '~> 4.2' to Gemfile and run command "bundle".

3. Make a file at config/initializers/ckeditor.rb and add this code:-

	Ckeditor.setup do |config|
  		# //cdn.ckeditor.com/<version.number>/<distribution>/ckeditor.js
  	config.cdn_url = "//cdn.ckeditor.com/4.6.1/basic/ckeditor.js"
	end

4. Add this code in view/layouts/application.html.erb:-

	<%= javascript_include_tag Ckeditor.cdn_url %>

5. Add this code in config/initializers/assets.rb:-

	Rails.application.config.assets.precompile += %w[ckeditor/config.js]

6. Make a view form and add this line:-

	<%= form.cktext_area :content, value: 'Default value', id: 'sometext' %>

7. Make a file at app/assets/javascripts/ckeditor/config.js 
   and add this code:-

	CKEDITOR.editorConfig = function (config) {
  		// ... other configuration ...

  		config.toolbar_mini = [
    			["Bold",  "Italic",  "Underline",  "Strike",  "-",  "Subscript",  "Superscript"],
  		];
  		config.toolbar = "mini";

  		// ... rest of the original config.js  ...
	}

   This code or file is usde to customize CKEditor's toolbar.

8. Now to add Emoji, add this line in app/assets/javascripts/application.js

	//= require ckeditor/init

	before 

	//= require_tree .

9. In view form add this line "ckeditor: {toolbar: 'Full'}" as:-

	<%= form.cktext_area :content, value: 'Default value', id: 'sometext', ckeditor: {toolbar: 'Full'} %>

10. Goto this link:-

	https://ckeditor.com/ckeditor-4/download/

    customize CKEditor by "Online Builder" as per your use and Download then extract.

11. You can see your customized CKEditor after openning "index.html" file from
    /Downloads/ckeditor_4.13.1_a13bc2f77cff/ckeditor/samples/

12. Copy the folder that you need like "lang", "skins" from:-

	/ckeditor_4.13.1_a13bc2f77cff/ckeditor

    and paste in the your projects folder

	Project/app/assets/javascripts/ckeditor/

13. Add the folders that you need in your project from:-

	ckeditor_4.13.1_a13bc2f77cff/ckeditor/plugins

    to

	Project/app/assets/javascripts/ckeditor/

14. Now run your server to see the magic.
