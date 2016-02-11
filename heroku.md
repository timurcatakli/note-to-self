# Note To Self - Heroku

  
# Hunter Commands Starts Here - needs to be edited and shit

eroku pg:reset DATABASE_URL
reset the database, drops and creates but it doest migrate or seed

reset the database even if there is no database
db:create does not work on heroku

now we have a database

heroku run rake db:migrate

heroku run rake db:seed

bundle install  if any problems with the gem

heroku logs

---------------------------

GEM for secrets:  dotenv

require 'dotenv'
Dotenv.load


root add a file called dotenv
convention is key capitilazied KEY1


git ignore is a big deal


# Hunter Commands Ends Here

-------

```
$ heroku login
Enter your Heroku credentials.
Email: ruby@example.com
Password:
...
```

```
$ heroku create
Creating polar-inlet-4930... done, stack is cedar-14
http://polar-inlet-4930.herokuapp.com/ | https://git.heroku.com/polar-inlet-4930.git
Git remote heroku added
```


```
$  git push heroku master
Fetching repository, done.
Counting objects: 10, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 876 bytes | 0 bytes/s, done.
Total 6 (delta 4), reused 0 (delta 0)

remote: -----> Ruby app detected
remote: -----> Compiling Ruby/Rails
remote: -----> Using Ruby version: ruby-2.2.4
remote: -----> Installing dependencies using 1.7.12
remote:        Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin -j4 --deployment
remote:        Fetching gem metadata from https://rubygems.org/...........
remote:        Fetching additional metadata from https://rubygems.org/..
remote:        Using rake 10.4.2
       ....
remote:        Bundle completed (38.43s)
remote:        Cleaning up the bundler cache.
remote: -----> Preparing app for Rails asset pipeline
remote:        Running: rake assets:precompile
remote: -----> Discovering process types
remote:        Procfile declares types -> web
remote:        Default types for Ruby  -> console, rake, worker
remote:
remote: -----> Compressing... done, 30.7MB
remote: -----> Launching... done, v16
remote:        https://pacific-river-8854.herokuapp.com/ deployed to Heroku
remote:
remote: Verifying deploy... done.
To git@heroku.com:polar-inlet-4930.git
   2e435c5..035d5f5  master -> master
```

```
$ heroku open
```


```
$ heroku logs --tail
Press Control+C to stop streaming the logs.
```

###Define a Procfile###

Use a ```Procfile```, a text file in the root directory of your application, to explicitly declare what command should be executed to start your app.

The Procfile in the example app you deployed looks like this:

```
web: bundle exec puma -C config/puma.rb
```

This declares a single process type, web, and the command needed to run it. The name web is important here. It declares that this process type will be attached to the HTTP routing stack of Heroku, and receive web traffic when deployed. The command used here is to run puma (the web server), passing in a configuration file.

Procfiles can contain additional process types. For example, you might declare one for a background worker process that processes items off of a queue.



