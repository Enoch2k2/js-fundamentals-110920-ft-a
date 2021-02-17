# Javascript Fundamentals

## Todays Agenda

- Variables - x
- ES6 Syntax
- Hoisting - x
- Functions - x
- Default Arguments - x
- Arrow Functions - x
- DataTypes - x
- Return - x
- Arrays - x
- callbacks - x
- Objects

### Variables

3 different kinds of variables

```
var - not safe, gets hoisted, can be redeclared, can be reassigned
let - safe, does not get hoisted, cannot be redeclared, can be reassigned
const - safe, does not get hoisted, cannot be redeclared, cannot be reassigned
```

### Hoisting

Javascript runs a file 2 seperate times, 1 to define everything and hoist. A second time to execute code.

Hoisting means to bring declaration to the top of the file in order for everything to be defined.

For exmaple:

```

var greeting = "hello"

```

would be hoisted to:

```
var greeting;

greeting = "hello"
```

Hoisting can be dangerous due to variables being used before given values, there is no errors for using a variable before giving it a value therefore makes debugging harder.

### Functions

Functions in javascript are like methods in ruby. They serve the same purpose. There are a few different ways to define functions.

```
function greeting() {
  console.log('hello world');
}
```

This way of defining functions get hoisted to the top of the page and is usable anywhere in your code.

Function definitions are also values and can be assigned to variables as well.

```

const greeting = function() {
  console.log('hello world');
}

```

Declaring a const to a function will obey the same laws that any other const obeys. This function will not be hoisted, you won't be able to redeclare greeting or reassign greeting as well.

Then we have the arrow function.

```

const greeting = () => {
  console.log('hello world');
  return 1+1; // with the {} code block attached to the => arrow function you must use the return keyword in order to return a value.
}

// and

const impliedReturnOfSum = (num1, num2) => num1 + num2;

with no {} and simple logic, you can use an implied return. In this example this function will automatically return num1 + num2;

impliedReturnOfSum(1, 3) // returns 4

```

You can also give default values, just like you would in Ruby:

```
function greeting(name = "developer") {
  console.log(`hello ${name}`) // take note that ` is the only string syntax we can interpolate with ${}
}

greeting("Bob") // logs hello Bob
greeting() // logs hello developer
```

### DataTypes

Here is a list of some of the different datatypes in JS:

```
Primitive Datatypes:
  1. Number
  2. String
  3. Undefined
  4. Symbol
  5. Null
  6. Boolean

Object Datatypes:
  1. Function
  2. Object
  3. Array
```

### Return

You must explicitly use `return` in a function unless it's an arrow funtion without a code block {}. If no `return` is given, the function will automatically give back `undefined`.

### Conditionals

Conditionals in Javascript are the same as Ruby with different syntax. In ruby we did:

```
 if 1 == 1
  puts "1 is equal to 1"
 elsif 1 == 2
  puts "1 is equal to 2"
 else
  puts "1 is not equal to 1 and 1 is not equal to 2"
 end
```

to re-write this in javascript, the conditions get wrapped in (), and have to specify our code blocks with {}

```
  if(1 == 1) {
    console.log("1 is equal to 1");
  }
  else if(1 == 2) {
    console.log("1 is equal to 2");
  } else {
    console.log("1 is not equal to 1 and 1 is not equal to 2");
  }
```

ternaries are exact syntax as ruby:

```
1 == 1 ? "1 is equal to 1" : "1 is not equal to 1";
```

case statements in ruby are known as switch statements in Javascript, in ruby we did:

```
  input = gets.strip

  case input:
    when "1":
      puts "user typed in '1'"
    else
      puts "user did not type in '1'"
    end
```

in Javascript, the syntax follows:

```
  let num = 1

  switch(num) {
    case 1:
      console.log('the num is 1');
      break;
    default:
      console.log('the num is not 1');
      break;
  }
```

Notice here that I am using break to break out of the switch statements. Without break it would run the logic of every case statement, break will break out of it. If you use return, you don't have to use break.

### Destructive vs Non Destructive

Descructive in javascript means to change the value of. For example in ruby a lot of times when we wanted something to be destructive, we'd use `!` at the end of the method call. For example:

```
  array = ["hello", "world"]
  array.map! {|element| element + "!"}
  array # array is now ["hello!", "world!"]
```

In Javascript, we have destructive functions and non-destructive functions.

### Arrays

Arrays are super similiar to ruby, with the exception that we can alter them or do non-destructive functions with them to give back a new array.

Destructive Functions:

```
  let array = ["hello"]

  array.push("world") // adds to end of array, ["hello", "world"]

  array.unshift("First Element") // adds to front of array ["First Element", "hello", "world"]

  array.pop() // removes from end of array ["First Element", "hello"]

  array.shift() // removes from front of array ["hello"]

  let newArray = [0,1,2,3,4,5]

  newArray.splice(1, 4) // removes elements starting at the 1 index, and 4 elements, [0, 5] is now newArray
```

Non Destructive Functions

```
  // We use the ... or spread operator in order to copy and paste elements of an existing array into a "new" array

  let array = ['hello']
  let array2 = [...array, 'world']
  let array3 = ['world', ...array]
  // array is still ['hello']
  // array2 is ['hello', 'world']
  // array3 is ['world', 'hello']

  let numberList = [0,1,2,3,4,5,6]

  // slice allows you to slice our a new array from an older array
  numberList.slice(1, 5) // returns [1,2,3,4,5]
  numberList // is still [0,1,2,3,4,5,6]
```

### Objects

Objects in Javascript are similiar to hashes in ruby with key / value pairs. For example:

```
  let howard = {
    name: "Howard",
    age: 21, /* for the record, no idea how old Howard is, probably 21 */
    profession: "Expert in the ways of Dad Jokes"
  }
```

However one added thing that javascript objects have that ruby hashes don't, are function definition values.

```
  let howard = {
    name: "Howard",
    age: 21, /* for the record, no idea how old Howard is, probably 21 */
    profession: "Expert in the ways of Dad Jokes",
    description: function() {
      console.log(`Hello my name is ${this.name}, i am ${this.age} years old, and my profession is ${this.profession}`)
    }
  }

  howard.description() // logs Hello my name is Howard, i am 21 years old, and my profession is Expert in the ways of Dad Jokes
```

You may of noticed the `this` keyword. We will go more into detail on that during the OO JS section, but for now, yes we use it like `self` in ruby. But it gets a lot more complicated in that as you will soon see :)
