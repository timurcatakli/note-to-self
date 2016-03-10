# (GitHub-Flavored) Markdown Editor

```
rails new delete-app
```
Start the server
```
rails s
```

Gem File
```
source 'https://rubygems.org'


gem 'rails', '4.2.5.1'
gem 'sqlite3'
gem 'sass-rails', '~> 5.0'
gem 'uglifier', '>= 1.3.0'
gem 'jbuilder', '~> 2.0'


gem 'ancestry'
gem 'rails_admin'
gem 'turbolinks'


group :development, :test do

  gem 'byebug'
end

group :development do

  gem 'web-console', '~> 2.0'
  gem 'spring'
end	
```

Bundle Install

Create models and migration
```
rails g migration create_restaurants
```
Migration File
```
class CreateRestaurants < ActiveRecord::Migration
  def change
    create_table :restaurants do |t|
      t.string :name
      t.string :address
      t.text :description
      t.timestamps
    end
  end
end
```

Run `rake db migrate`

Define the model - restaurant.rb
```
class Restaurant < ActiveRecord::Base
end
```

Create a restaurant in the console
```
Restaurant.create name: 'Cha Cha Cha'
```

Let's create an ADMIN Page using rails_admin
```
rails g rails_admin:install
```

Run the server
