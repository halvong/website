Bootstrap, George Lomidze, Packtpub
9/05/2020, Sat

4:07

#url
https://subscription.packtpub.com/video/web_development/9781800201521/p4/video4_2/-navbar

#steps
1. docker-compose exec web rails g controller hotel index  

#Notes
Look for stripeToken, authenticity_token

#you should see this
hidden tags
    scrf-token
    stripe-public-key


#Rails Stripe
1. docker run -i -t --rm -v ${PWD}:/usr/src/app ruby:2.7.1 bash
   gem install rails -v 5.2.4.3
   rails new <name> -d postgresql --no-ri --no-rdoc
   exit
2. docker build -t docker_rails .

3. Gemfile, pg75 
	gem 'pg', '~> 1.0'
    
4. docker-compose run --rm database psql -U tom -h database
   docker-compose rm -f database
   docker-compose up -d database
   docker-compose up -d --force-recreate web
   docker-compose up -d --force-recreate database
   
5. docker volume [ls rm]
6. docker-compose exec web rails g scaffold Product name description:text secret:text
6b. gem 'devise', '~> 4.2'
    gem 'bcrypt'
    gem 'bootstrap-sass', '~> 3.3', '>= 3.3.7'
    gem 'stripe', '~> 4.21', '>= 4.21.2'
    
7. docker-compose exec web rails db:migrate
8. docker-compose exec web rails g devise:install -- 2.2 
   docker-compose exec web rails g devise:views   -- 2.2 
9. docker-compose exec web rails g devise User stripe_id stripe_subscription_id card_brand card_last4 card_exp_month card_exp_year expires_at:datetime 
   docker-compose exec web rails db:migrate
10. getbootstrap.com

11. app/assets/javascripts/application.js
        //= require jquery
        //= require jquery_ujs

11. docker-compose run web bash
        EDITOR="vi" bin/rails credentials:edit
        
        See LastPass 
    
12. app/views/layouts/application.html.erb L10  
        <%= javascript_include_tag 'application', 'https://js.stripe.com/v2/', 'data-turbolinks-track': 'reload' %>
        <%= tag :meta, name: "stripe-public-key", content: Rails.application.credentials.stripe_public_key %>
13. create config/initializers/stripe.rb
        Stripe.api_key = Rails.application.credentials.stripe_private_key
14. docker-compose exec rails c
        Stripe::Customer.all        
        
15. docker-compose exec web rails db:migrate VERSION=0
16. docker-compose exec web rails db:migrate:status
17. docker-compose exec web rails g model Subject 
    docker-compose exec web rails g model Page 
    docker-compose exec web rails g model Section 
    docker-compose exec web rails db:migrate
    
18. docker-compose exec web rails g migration AlterUsers 
    docker-compose exec web rails db:migrate
 
     
#Rails Current
1. demo controller w/ index view
   docker-compose exec web rails g controller demo index 
   docker-compose exec web rails g controller grand index
 
2. a. simple route - get "demo/index" or match "demo/index", :to => "demo#index", :via => :get 
   b. default route - :controller/:action/:id 
                      /students/edit/52
                      StudentsController, edit action, id=52
                      ---
                      get ':controller(/:action(/:id))'
                      match ':controller(/:action(/:id))', :via => :get
                      ---
   c. root route - match "/", :to => "demo#index", :via => :get     
                   ---   
                   root "demo#index"
                   
   d. resourceful route
   
3. Render template 
    def index
        render('index')
        render(:template => 'demo/hello')
        render('demo/hello')
        render('hello')
   end   
4. Redirect actions   

    def other_hello
        redirect_to(:controller => 'demo', :action => 'index') 
        redirect_to(:action => 'index') 
    end
5. View templates
    <%= 1 + 1 %>
    <% target = "world" %>

6. <link href="/assets/stylesheets/application.css" rel="stylesheet" type="text/css" media="all" />
   <%= stylesheet_link_tag('application') %> 
   <%= stylesheet_link_tag('application', :media=> 'all') %> 
7. link   
   <%= link_to "Home", {:action => 'index'}, :class=>"current" %>
8. URL
    params['page'] or params[:page]
9. rails g migration DoNothingYet 
    def up
    end
    
    def down
    end
    
10. docker-compose exec web rails g model ModelName    
    docker-compose exec web rails g model User    

11. rails db:migrate   
    docker-compose exec web rails db:migrate:status  
    rails db:migrate VERSION=0   
    rails db:migrate VERSION=xxxxxxxxxxxxxxxx  
    
12. docker-compose exec web rails console 


   
#Git   
1. show log 
   git log --oneline
   
2. git config --global -e

3. modify commit 
   git commit --amend -m "hello world" (before push to origin)
   
4. Switch remote URL 
   git remote -v
   git remote set-url origin https://github.com/USERNAME/REPOSITORY.git 
   
5. git difftool <head commit> <previous commit>
   git diff <head commit> <previous commit>
   
6. git fetch origin --prune   
7. git merge --squash <branch>

