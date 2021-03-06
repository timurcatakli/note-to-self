# Note To Self - Active Record - Rake - SQLite3

  
# Bundle Commands

```bash
be = shortcut for bundleexec

be rake db:create && be rake db:migrate
$ bundle exec rake generate:migration NAME=create_ratings
$ bundle exec rake generate:migration NAME=remove_from_dogs
$ bundle exec rake generate:migration NAME=rename_raterid
```


**If the migration name is of the form “AddXXXToYYY” or “RemoveXXXFromYYY” and
is followed by a list of column names and types then a migration containing
the appropriate add_column and remove_column statements will be created.**

### Rake Steps
- Write the bundle exec rake command (see above) for the migration file
- Run the migration file below

```bash
$ bundle exec rake db:migrate ...
```

- Check your tests :
```bash
$ bundle exec rspec spec/schema/dogs_table_spec.rb
```

- Access the SQLite3 DB. We can always access our database through the SQLite3 console where we can view our database schema and the details for each of our tables

```bash
$ sqlite3 db/database.sqlite3
```

```bash
$ sqlite PRAGMA table_info(dogs);
```

#Active Record Commands

```bash
Dog.all
```

```bash
Dog.where(age: 1)
```

```bash
Dog.where("age = ? and name like ?", 1, '%Te%')
```

```bash
Dog.order(age: :desc)
```

```bash
Dog.limit(2)
```

```bash
Dog.count
```

```bash
Dog.pluck(:name, :age)
```

```bash
Dog.first
```

```bash
Dog.find(3)
```

```bash
Dog.find_by(name: "Jayda")
```
```bash
Dog.order(name: :asc).where(age: 1).limit(1)

```

#Rake Methods
```bash
Bash Command: be rake -T
```

```bash
rake console             # Start IRB with application environment loaded
rake db:create           # Create the database
rake db:drop             # Drop the database
rake db:migrate          # Migrate the database
rake db:rollback         # rollback your migration--use STEP=number to step back multip...
rake db:seed             # populate the database with sample data
rake db:version          # Returns the current schema version number
rake generate:migration  # Create an empty migration in db/migrate, e.g., rake generate...
rake generate:model      # Create an empty model in app/models, e.g., rake generate:mod...
rake generate:spec       # Create an empty model spec in spec, e.g., rake generate:spec...
rake spec                # Run the spec suite
```

# Active Record Table Related Commands

```bash
ActiveRecord::Base.connection.tables

[
    [0] "schema_migrations",
    [1] "todos"
]
```


```bash
Dog.connection

Todo.column_names

[
    [0] "id",
    [1] "description"
]
```

### Save!
Save!: It saves and raises an error
Save: Simply saves and do not raise an error



Below method forces to save after increase
```
def age!
self.age += 1; self.save
end
```




### Find

find_by_id(1) and find(1) are pretty much the same except
find_by_id(1) returns nil.


### Postgres

which postgres terminal command
```
>>$ /usr/local/bin/postgres
```

### Has_many, through, source

```ruby
class User
  has_many :subscriptions
  has_many :newsletters, :through => :subscriptions
end

class Newsletter
  has_many :subscriptions
  has_many :users, :through => :subscriptions
end

class Subscription
  belongs_to :newsletter
  belongs_to :user
end
```

With this code, you can do something like Newsletter.find(id).users to get a list of the newsletter's subscribers. But if you want to be clearer and be able to type Newsletter.find(id).subscribers instead, you must change the Newsletter class to this:

```ruby
class Newsletter
  has_many :subscriptions
  has_many :subscribers, :through => :subscriptions, :source => :user
end
```
