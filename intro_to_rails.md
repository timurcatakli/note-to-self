# Note To Self - Intro to Rails

  
# Setting Up a Rails App

```bash
rails new APP_NAME --skip-spring --database=postgresql --skip-test-unit
```

Rails app starts from `boot.rb` and then goes to `application.rb`.

In `application.rb` you might consider disabling the frameworks you don't need. If you don't need to send emails you may want to disable `action_mailer...`

```
module TestApp
  class Application < Rails::Application
    config.active_record.raise_in_transactional_callbacks = true
  end
end

```

Rails named our app as TestApp as the **namespace**

Under config/environment we have different environments like `development`, `production`, `testing`

`database.yml` file

`secrets.yml` file for session authorization and encryption

`initializers` are for assetpipeline

## Gem File

As a beginner you might not need the following gem files:

`gem 'coffee-rails', '~> 4.1.0'`

`gem 'jbuilder', '~> 2.0`

`gem 'sdoc', '~> 0.4.0', group: :doc`

## Routes.rb

```ruby
get '/info' => static#info'

means

Prefix	Verb 	URI Pattern     	Controller#Action
info  	GET  	/info(.:format) 	static#info
```

Once we have the prefix we can use it the following way:

`app.info_path` or `app.info_url`

To get the routes use `be rake routes`

static controller and info action does not exist so lets generate it.

`be rails generate controller static info`

## Creating a database

```bash
be rake db:create db:migrate
```

## Asset Pipeline

**application.html.erb** is where all included files are managed...

```html
<!DOCTYPE html>
<html>
<head>
  <title>TestApp</title>
  <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
  <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
  <%= csrf_meta_tags %>
</head>
<body>

<%= yield %>

</body>
</html>
```
