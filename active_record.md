# Note To Self - Active Record - Rake - SQLite3

## Table of Contents
  - [First Page](readme.md)
  - [Git Steps & Commands](#Git Steps & Commands)
  





# Bundle Commands

```bash
$ bundle install
$ bundle exec rake db:create
$ bundle exec rake db:migrate
```

### Rake Migration File Creator Sample Commands
Following will create migration files with a timestamp in the file name


```bash
$ bundle exec rake generate:migration NAME=create_people
$ bundle exec rake generate:migration NAME=create_dogs
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

