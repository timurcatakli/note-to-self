# Constructors

A more convenient way to create objects that derive from some shared prototype is to use a constructor. In JavaScript, calling a function with the new keyword in front of it causes it to be treated as a constructor. The constructor will have its this variable bound to a fresh object, and unless it explicitly returns another object value, this new object will be returned from the call.

An object created with new is said to be an instance of its constructor.

Here is a simple constructor for rabbits. It is a convention to capitalize the names of constructors so that they are easily distinguished from other functions.

```javascript
function Rabbit(type) {
  this.type = type;
}

var killerRabbit = new Rabbit("killer");
var blackRabbit = new Rabbit("black");
console.log(blackRabbit.type);
// → black
```

```javascript
function Tree(){
  this.age = 0;
  this.height = 0;
  this.name = "Orange Tree";
  this.orangeCount = 0;
  this.isAlive = true;
};

Tree.prototype.grow = function(){
  this.age += 1;
  this.height += 10;

  if (this.age >= MAX_AGE){
    this.isAlive = false;
  };  

  if (this.age < FRUIT_BEARING_AGE){

  } else {

    if (this.isAlive === true){
      this.orangeCount += Math.floor(Math.random() * 10) + 1;
    }
  };


};

Tree.prototype.dropOrange = function(){
    this.orangeCount -= 1;
};
```

```javascript
var tree = new Tree();
console.log("Age : " + tree.age);
console.log("Height : " + tree.height);
console.log("Orange Count : " + tree.orangeCount);
console.log("Alive : " + tree.isAlive);
console.log("=============TREE GROWS 1 YEAR===================");
tree.grow();
console.log("Age : " + tree.age);
console.log("Height : " + tree.height);
console.log("Orange Count : " + tree.orangeCount);
console.log("Alive : " + tree.isAlive);
console.log("=============TREE GROWS 3 YEARS===================");
tree.grow();
tree.grow();
tree.grow();
console.log("Age : " + tree.age);
console.log("Height : " + tree.height);
console.log("Orange Count : " + tree.orangeCount);
console.log("Alive : " + tree.isAlive);

```
