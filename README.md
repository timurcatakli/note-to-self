# Note To Self - Web Development Cheatsheet

## Table of Contents
  - [Git Steps & Commands](#Git Steps & Commands)
  - [My GIT Workflow](#my-git-workflow)
  - [Ruby Commands](#ruby-commands)
  - [Benchmarking](#benchmarking)
  - [Big O - Binary Search](#big-o---binary-search)
  - [SQLITE3 CREATE, ALTER, UPDATE METHODS](#sqlite3-create-alter-update-methods)
  - [Objects Array](#objects-array)
  - [Metaprogramming](#metaprogramming)
  - [Yield in Ruby Basics](#yield-in-ruby-basics)
  - [Sqlite3 Ruby Interface](#sqlite3ruby-interface)
  - [Active Record - Rake - SQLite3](#https://github.com/timurcatakli/note-to-self/blob/master/active_record.md)
  

# GIT STEPS & COMMANDS

```Bash
git init
```

```ruby
git status
```
```ruby
git add
```
```
git commit . -m “Message goes here”
```

To see which remote servers you have configured, you can run the

```
git remote -v
```

command. It lists the shortnames of each remote handle you’ve specified. If you’ve cloned your repository, you should at least see origin – that is the default name Git gives to the server you cloned from:

**Create a new repo on github.com and do the following:**
```
git remote add origin https://github.com/timurcatakli/lucky_numbers.git
```
```
git push -u origin master
```
```
Delete an origin
```
```
git remote rm origin
```

###Removing or disabling GIT
All the data git uses info is stored in .git/ , so removing it should work just fine. Of course, make sure that your working copy is in the exact state that you want it, because everything else will be lost. From there, you can run git init to create a fresh repository. 
```
rm -rf .git 
```
should suffice


### MY GIT WORKFLOW

CLONE THE REPO TO LOCAL HARDDRIVE
```
git clone …github.repo.url
```
MASTER is already created - create a new branch called “dev” and switch into it
```
git checkout -b “dev”
```
CONTINUE WORKING ON “DEV”, ONCE YOU MAKE A PROGRESS ADD-COMMIT

```
git add .
git commit . -m “A nice explanatory msg goes here”
```

switch to master and merge “dev” with “master

```
git checkout master
git merge dev
```

switch back to “dev” and continue working - this way you always have a working copy on master and if you make a mistake you may revert back - once you are done,  **push to origin** and **delete the branch 'dev'**



# RUBY COMMANDS


#### Ruby interactive help bash terminal
```ruby
ri -i
```
#### Ternary Operator

Ruby also has something called a **"ternary operator"** which provides a shortcut way of making basic comparisons. The syntax of this is a condition, followed by a question mark, followed by the expression that should be given if the condition is true, followed by a colon, followed by the expression that should be given if the condition is false, as can be seen below:

```
condition ? true_expression : false_expression
```

#### :foo
:foo is a **symbol** named "foo". Symbols have the distinct feature that any two symbols named the same will be identical:
```ruby
"foo".equal? "foo"  # false
```
```ruby
:foo.equal? :foo    # true
```
This makes comparing two symbols really fast (since only a pointer comparison is involved, as opposed to comparing all the characters like you would in a string), plus you won't have a zillion copies of the same symbol floating about.

***Also, unlike strings, symbols are immutable.***


#Benchmarking


![Benchmarking](images/benchmarking.png "Benchmarking")


#Big O - Binary Search

![Big O - Binary Search](images/bigo.png "Big O - Binary Search")


#SQLITE3 CREATE, ALTER, UPDATE METHODS


```sql
CREATE TABLE friends (
  id INTEGER,
  name STRING,
  birthday DATE);
 ```
 
```sql  
INSERT INTO friends (id, name, birthday) VALUES
(1, 'Jane Doe', 'May 19th, 1993');
```
```sql  
INSERT INTO friends (id, name, birthday) VALUES
(2, 'Joe Doe', 'May 18th, 1994');
```

```sql  
INSERT INTO friends (id, name, birthday) VALUES
(3, 'Frank Roosevelt', 'May 11th, 1995');
```

```sql  
UPDATE friends
SET name = "Jane Smith"
WHERE id = 1;
```

```sql  
ALTER TABLE friends ADD email STRING;
```

```sql  
UPDATE friends
SET email = 'jsmith@example.com'
WHERE id = 1;
```

```sql  
UPDATE friends
SET email = 'jdoe@example.com'
WHERE id = 2;
```

```sql  
UPDATE friends
SET email = 'froosevelt@example.com'
WHERE id = 3;
```

```sql  
DELETE FROM friends WHERE id = 1;
```

```sql  
SELECT * FROM friends;
```
Give me the hire date, first name, and last name of all employees hired before February 15, 2011

```sql
SELECT hire_date, first_name, last_name FROM employees WHERE hire_date < '2011-02-15'
```

Give me a list of all employees whose name begins with "A"

```sql
SELECT * FROM employees WHERE first_name LIKE 'A%'
```

Give me a list of every track where composer is blank
```sql
SELECT * FROM tracks WHERE composer IS NULL
```

Give me a list of the 10 most expensive invoices from Germany
```sql
SELECT * FROM invoices WHERE billing_country = 'Germany' ORDER BY total DESC LIMIT 10
```


Find the number of invoices sent to the city of "Santiago"

```sql
SELECT COUNT(id) FROM invoices WHERE billing_city = 'Santiago'
```

**SQL Inner Join**

```sql
SELECT artists.name, albums.title
FROM artists
INNER JOIN albums
ON artists.id = albums.artist_id;
```




# SQL Naming Conventions

Technically you can use any field names and table names you want, but there are some conventions that are generally followed for sanity.

- Table names are pluralized, e.g., "students," "products," "todos," etc. Each row is uniquely identified by an automatically-incrementing integer field called id. ActiveRecord migrations (Links to an external site.)do this for you automatically, but you'll have to be explicit when designing your tables by hand.

- Fields are named using snake_case, rather than camelCase. The latter looks weird and out of place in Ruby.

- Fields that involve dates or times end in _at or _on (created_at, updated_at, completed_at, etc.) unless it's really obvious they already refer to something time-related. For example, it's more common to say birthday thanborn_on.

- When in doubt, make your field and table names as self-explanatory as possible. Avoid field names like type,kind, status, etc. They could refer to anything! Err on the side of clarity, even if it seems verbose. Other programmers will appreciate it, and computers don't care if your field name is 20 characters long rather than 5 characters long.

- Rails includes created_at and updated_at fields by default, which record when a row is first added to a table and when it was last updated. They are good to include for records, so they will often be included in schemas.
Primary Keys

- Each row in a database table should have a primary key. This is a field (or collection of fields) which uniquely identify that row from all other rows. Rails defaults to using a synthetic primary key, which is just an arbitrary, auto-incrementing integer usually denoted by the field name id. It's called "synthetic" because it doesn't have any inherent meaning.

- The assumption that the primary key is an auto-incrementing integer called id is baked deeply into Rails. Most web applications follow this convention.

**Foreign Keys**

Foreign keys are used to connect one table to another. Generally they will be used to connect a primary key (ie. id) to another table with a field for that primary key as well. (region_id for example).


# Objects Array
tim
```ruby
class DVD
  @@array = Array.new
  attr_accessor :title, :category, :runTime, :year, :price 

  def self.all_instances
    @@array
  end

  def initialize()
    @title = title
    @category = category
    @runTime = runTime
    @year = year
    @price = price
    @@array << self
  end
end
```

```ruby
DVD.new
DVD.new
DVD.new
```

```ruby
DVD.all_instances
```
#Metaprogramming


Metaprogramming, used wisely, has great value; ease of metaprogramming is a strong argument in favor of dynamic typing.


# Yield in Ruby Basics


The yield method allows us to pass behaviour into a method, it makes methods much more flexible.

Common ruby methods like **each** use yield.


**Example 1: The simplest yield ever**

Define the method with a yield
```ruby
def yield_method_1
  yield 
end
```
call the method and send it behavior
```ruby
p yield_method_1 {puts "this is behaviour being passed in"}
```

**Example 2: Passing block variable into a yield**

the value of this variable is set in the yield

```ruby
def yield_method_2
  yield 15
  puts "additional code goes here"
end
```
```
p yield_method_2 { |num|  
  puts "This is behaviour being passed in."
  puts "It using a block var with value #{num}"
  }
```

**Example 3: working with arrays and loops - passing the array as an argument** 

```ruby
def yield_method_3(nums)
  while nums.length > 0
    item = nums.pop 
    yield item
  end
end
```
```ruby
my_nums =[1,2,5]

p yield_method_3(my_nums) {|num| puts "The last value in the array is : #{num}"}

```
# Managing Dependencies

An object has a dependency when it knows:
- The name of another class
- The name of a message that it intends to send to someone other than self
- The arguments that a message requires
- The order of those arguments

With OOP, your goal is to manage dependencies so that each class has the fewest possible -- a class should know just enough to do its job and not one thing more.

Here are some techniques for reducing dependencies in your code:

### Injecting Dependencies

"Dependency Injection" is a 25-dollar term for a 5-cent concept. Dependency Injection is the design of objects where they receive instances of the objects from other pieces of code instead of constructing them internally.

So, instead of:
```ruby
class Car
  def initialize
    @driver = Person.new
  end
end
```

We "inject" the dependency in the constructor:
```ruby
class Car
  def initialize(person)
    @driver = person
  end
end
```

This means that any object implementing the interface which is required by the object can be substituted in without changing the code, which simplifies testing, and improves decoupling. It's a very useful technique for testing, since it allows us to isolate classes and mock or stub out dependencies easily.

### Isolating Dependencies

When a class contains embedded references to a message that is likely to change, isolating the reference provides some insurance against being affected by that change.

Starting with:
```ruby
def Car
  def driver_comfort
    foo = some_intermediate_result * driver.age
  end
end
```

We isolate the external message by wrapping it in another method:
```ruby
def Car
  def driver_comfort
    foo = some_intermediate_result * driver_age
  end

  def driver_age
    driver.age
  end
end
```

Now if the interface of driver changes, we will only have to alter our Car class in one place. Although not every external method is a candidate for this preemptive isolation, it’s worth examining your code, looking for and wrapping the most vulnerable dependencies.

An alternative way to eliminate these side effects is to avoid the problem from the very beginning by reversing the direction of the dependency.

### Remove argument-order dependencies

We have three arguments that need to be passed in order.
```ruby
def initialize(color, manufacturer, driver)
  @color        = color
  @manufacturer = manufacturer
  @driver       = driver
end
```

Instead, we use hashes for initialization arguments. The order of arguments is no longer fixed.
```ruby
def initialize(args)
  @color        = args[:color]
  @manufacturer = args[:manufacturer]
  @driver       = args[:driver]
end
```

Even better, explicitly define defaults:
```ruby
def initialize(args)
  @color        = args.fetch(:color, "white")
  @manufacturer = args.fetch(:manufacturer, "Toyota")
  @driver       = args[:driver]  
end
```

### Dependency Inversion
Be conscious about the direction of your dependencies -- build classes that depend on things that change less often than they do.

The Dependency Inversion Principle is primarily about reversing the conventional direction of dependencies from "higher level" components to "lower level" components such that "lower level" components are dependent upon the interfaces owned by the "higher level" components. (Note: "higher level" component here refers to the component requiring external dependencies/services, not necessarily its conceptual position within a layered architecture.) In doing so, coupling isn't reduced so much as it is shifted from components that are theoretically less valuable for reuse to components which are theoretically more valuable for reuse.


# Class Inheritance & Passing Custom Arguments

```ruby
class Bicycle
  attr_reader :size, :chain, :tire_size

  def initialize(args={})
    @size       = args[:size]
    @chain      = args[:chain]     || default_chain
    @tire_size  = args[:tire_size] || default_tire_size
  end

  def default_chain       # <- common default
    '10-speed'
  end

  def default_tire_size
    raise NotImplementedError
    
  end

end

class RoadBike < Bicycle
  # ...
  def default_tire_size   # <- subclass default
    '23'
  end
end

class MountainBike < Bicycle
  # ...
  def default_tire_size   # <- subclass default
    '2.1'
  end
end
```
```ruby
road_bike = RoadBike.new(
              size:       'M',
              tape_color: 'red' )

p road_bike.tire_size     # => '23'
p road_bike.chain         # => "10-speed"

mountain_bike = MountainBike.new(
                  size:         'S',
                  front_shock:  'Manitou',
                  rear_shock:   'Fox')

p mountain_bike.tire_size # => '2.1'
p road_bike.chain         # => "10-speed"
```


# SQLite3/Ruby Interface

This module allows Ruby programs to interface with the SQLite3 database engine (www.sqlite.org).

You must have the SQLite engine installed in order to build this module.

Note that this module is only compatible with SQLite 3.6.16 or newer.


```ruby
require "sqlite3"

# Open a database
db = SQLite3::Database.new "test.db"

# Create a database
rows = db.execute "create table numbers (\nname varchar(30),\nval int\n);\n"

# Execute a few inserts
{
  "one" => 1,
  "two" => 2,
}.each do |pair|
  db.execute "insert into numbers values ( ?, ? )", pair
end

# Execute inserts with parameter markers
db.execute("INSERT INTO students (name, email, grade, blog) 
            VALUES (?, ?, ?, ?)", [@name, @email, @grade, @blog])

# Find a few rows
db.execute( "select * from numbers" ) do |row|
  p row
end
```