# ruby-training
Ruby/Rails Practice

-------------------------------------------------------------------------------------
Notes on Ruby on Rails Dev Environments
-------------------------------------------------------------------------------------

                Terminal Commands

sinfamous:~/workspace/taski (master) $ rails s -b $IP -p $PORT
Command to run Rails server in C9 ^

sinfamous:~/workspace/taski (master) $ rake db:create:all^C
Command to create databases

sinfamous:~/workspace/taski (master) $ rails/rake db:migrate
Command to run migration for current environment

sinfamous:~/workspace/taski (master) $ rake db:setup
Command to run db:scheme:load, db:seed - Erase test data, restart environment

---------------------------------------------------------------------------------
                Querying Database

Project.find(title: "Text")                  Find Project with a title of "Text"
Project.where(title: "Project 2")            Find Project where Title = Project 2 
Project.first() / Project.last()            Find First Project in sys. Find Last Project in sys.

Project.each do |e|             For each project
    puts e.description          print project attribute description
end                             end statement


---------------------------------------------------------------------------------
                
                    Routes
                
rake routes
    Pulls all routes in current database, detailed listing
    Sample Output
    
    Prefix Verb     URI Pattern                                                                              Controller#Action
                
           projects GET    /projects(.:format)                                                              projects#index
                    POST   /projects(.:format)                                                              projects#create
        new_project GET    /projects/new(.:format)                                                          projects#new
       edit_project GET    /projects/:id/edit(.:format)                                                     projects#edit
            project GET    /projects/:id(.:format)                                                          projects#show
            PATCH  /projects/:id(.:format)                                                                  projects#               
            PUT    /projects/:id(.:format)                                                                  projects#update
            DELETE /projects/:id(.:format)                                                                  projects#destroy
rails_service_blob GET    /rails/active_storage/blobs/:signed_id/*filename(.:format)                        active_storage/blobs#show


------------------------------------------------------------------------------------------------------------------------------------------


Adjusting routes

Generate routes using
    rails g controller Pages contact about home

    Rails.application.routes.draw do
  get "contact", to: "pages#contact"
  get "about", to: "pages#about"
  
Redirecting
  get "blog", to: redirect("http://sdmtech.wordpress.com")

<h3>Go back to <%= link_to "homepage", root_path %></h3>
 Sample inline redirect
    link_to creates an html link of the word in quotes
        root_path is the destination - homepage is linked to root (prefix), 
        and _path is syntax for this


----------------------------------------------------------------------------------------------------------------------------------


    <%= render "shared/nav" %>
Render a file (shared folder, nav file (_nav.html.erb)) using erb

    <% image_tag ("logos/logo.png", width: '150px') %>
Render an image (logos folder, logo.png file, format width)

------------------------------------------------------------------------------------------------------------------------------------------------


Code placed in application.html.erb is universal - applies to all pages as it is a 
    default layout section
    
    
    
    
entered into application.rb, config file    
    
    config.assets.enabled = true
    config.assets.paths << Rails.root.join('/app/assets/fonts')

entered into css/scss file. Tells the file what font to use, and where to access it
once it is added to the filetree.
    
    @font-face {
        font-family: "Roboto Condensed";
        src: url('/assets/Roboto_Condensed');
    }
    
    
    Enabling Assets in Config
    Going into Assets, and adding this fonts directory to the array that is used

------------------------------------------------------------------------------------------------------------------------


    validates_presence_of - Sets a form or action to require the fields set in order to pass
                        Useful for verifying in models
                        

    has_many :tasks - Integrates Tasks model with project model (Active Record Association)
