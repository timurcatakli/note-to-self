# Rails as an API Server

* Create new rails app
* Create a new namespace for API in `Routes`

```ruby
Rails.application.routes.draw do

namespace :v1 do
	resources :api
end
```

`be rake routes`

* Create appropriate controller

`be rails g controller v1/api index show new edit create update destroy'

**It created its own v1 namespace..**

Add a conditional constraint in the namespace so that it only accepts JSON

```ruby
Rails.application.routes.draw do

FORMAT_JSON = ->(r) {r.format == 'json' }

namespace :v1, constraints: FORMAT_JSON do
	resources :api
end
```

* The constraint above is a lambda code. To test it go to:

```ruby
$ rails console
$ app.get 'v1/api' #=> should give 404
$ app.get 'v1/api.json' #=> should work
```

```ruby
->(r) {r.format == 'json' } #this is a method, an anonymous function

# it is equal to
def x(r)
r.format == 'json'
end

-> #arrow is a ruby thing...
x = ->{ 5 }
x.call #=> 5

#another example is

plus = -> ( a, b ){ a + b }
plus.call(10,15) #=> 25, creates an anonymous function that can be called

Routes are not class so we can not use a method and then call it...
```

In the API controller 

```ruby
class V1::API < ApplicationController

	def index
    	render json: Product.all
    end
    
    def show
	    render json: Product.find(params[:id]
    end


end
```

If you dont have a Product model here is how you can generate one real quick:

```
be rails g model Product name:string size:integer
be rake db:migrate

be rails console

10.times{ |n| Product.create!(name: "Product ##{n+1}", size: n)
```

In order to test the JSON

```ruby
rails console
app.get '/v1/api #=> Should give error
app.get '/v1/api.json #=> Should give work
app.response #=> should give all json data
app.response.type
app.response.body
```

```javascript
$(function(){

	$('ol.products').each(function(){
    
    	var ol = $(this);
        
        $.getJSON('v1/api').then(function(products){
        	var lis = products.map(function(product) {
            // this creates an LI for us 
            	return $('<li>').text(product.name); 
            });
            
            ol.append(lis);
            
        });
    
    });
    

})
```
