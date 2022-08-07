alert() # function

console.log("hello world!") # function

console.log(typeof 23) # return Number

console.log(typeof 'apple') # return String

console.warn("something/variable/expression") # show warning if there is one

console.error("something/variable/expression") # show error if there is one

console.table(object) # show object in the form of table

<strong>The 7 Primitive Data Types:</strong>
- Number: Floating point numbers 👉 Used for decimals and integers
- String
- Boolean
- Undefined 👉 <span style="color: green">let</span> children; 
- Null
- Symbol: Value that is unique and cannot. be changed [Not useful for now]
- BigInt: Larger integer

Number("1990") # convert string to **Number**
String(23) # convert number to **String**
Boolean("apple") # convert to **Bool**

**Falsy values:** 
- false
- 0
- ""
- undefined
- null
- NaN

**===** is strict equal operator 👉 18 === 18 return true
**==** is loose equal operator 👉 "18" == 18 return true

const favourite = promt("What's your favourite number?") # ask user to input sth

````JavaScript
conts day = "Monday";
switch (day) {
  case "Monday":
    console.log("It is Monday")
    break
   case "Tuesday":
   case "Wednesday":
    console.log("If it is either Tuseday or Wednesday, print this line");
    break
   default:
    console.log("Print default value.")
}
````
An **Expression** is a piece of code that produce value.

```` JavaScript
# Ternary operator
true ? "do this if true" : "do this if false" ;
````
**'use strict'** 👉 used for declaring strict mode in JavaScript; has to put it at the very top of the script. We should always use strict mode when working with JavaScript because some errors won't show without strict mode.
- first, strict mode forbids us to do certain things
- second, it creates visible errors in the devloper console while in other situation JavaScript would just fail silently.

```` JavaScript
// Function declaration; note: you can call this type of function before you declare it.
function calcAge1(birthYear){
  return 2037 - birthYear;
}

// Function expression; it similar to lambda in python or computable property in swift
const calAge2 = function (birthYear) {
  return 2037 - birthYear;
}

// let's call the functions 
const age1 = calcAge1(1990);
const age2 = calcAge2(1990);


// Arrow function; Note: arrow function doesn't work with this keyword
const calcAge3 = birthYear => 2037 - birthYear;
const age3 = calcAge3(1990);
````
👉 use **backtick** like f string in python and string interpolation in swift. Ex: `some string ${variable}` 

````JavaScript
// two ways to create an array
const friends = ['Ross', 'Monica', 'Joey']
const otherFriend = new Array('Rachel', 'Phoebe', 'Chandler')

// get the length of the array
const numberOfFriend = friends.length

// add value to the last index
friends.push("newFriend"); // this will add a newFriend to the array and return the length

// add an element to the beginnin of the array
friends.unshift('John');

// remove the last element of the array
friends.pop(); // it returns the element that it removes

// remove the first element from the array
friends.shift();

// find the index of the element
friends.indexOf("Ross"); // note: if the argument is not in the array, it return -1

// check if an element is in the array or not
friends.include("Ross") // return true
friends.include("Angela") // return false
````

````JavaScript
// JavaScript object is like the dictionary in Python
  const student = {
    firstName: 'John',
    lastName: 'Shelby',
    age: 29,
    job: 'Peaky Blinder',
    brothers: ['Tommas Shelby', 'Authur Shelby', 'Finn Shelby']
  }
  
  // use dot notation to call the object
  console.log(student.firstName);
  
  // use bracket notation
  console.log(student["firstName"]);
  // or 
  const nameKey = "Name";
  console.log(student["first" + nameKey]); // note: we can use expression inside the bracket.
  
  // add new key-value pair
  student.address = "Birmingham";
  // or
  student["company"] = "Shelby Brothers Limited";
  
  // function can be used as a property in JavaScript's object
    const student = {
    firstName: 'John',
    lastName: 'Shelby',
    age: 29,
    job: 'Peaky Blinder',
    brothers: ['Tommas Shelby', 'Authur Shelby', 'Finn Shelby'],
    calcAge: function (birthYear) {
      return 2037 - birthYear;
    }
  }
  
  console.log(student.calcAge(1990));
  // or
  console.log(student["calcAge"](1990));
  
````

````JavaScript
// for loop
for(let counter = 1; counter <= 10; count++) {
  console.log(`Lifting weights repetition ${counter} 🏋️‍♀️`);
}

// loop backward 
const student = [
  "John",
  "Shelby",
  26,
  "Peaky blinder",
  ["Tommas Shelby", "Authur Shelby"],
];

for (let i = student.length -1; i >= 0; i--) {
  console.log(student[i]);
}

````

**Arrow Function** doesn't have its own "this" keyword; if you use "this" inside arrow function, the "this" keyword is belong to its parents. This means that we should never use Arrow Function as the method; we instead use the regular function.

**Copying Object**
````JavaScript
const john = {
firstName: 'John',
lastName: 'Shelby',
age: 27
}
// now let's copy
const johnCopy = join;
// now let's change the value of the age
johnCopy.age = 25
// now let's print jonh and jonhCopy
console.log(jonh); // outcome: { firstName: 'John', lastName: 'Shelby', age: 25}
console.log(jonhCopy); // outcome: { firstName: 'John', lastName: 'Shelby', age: 25}
// what we see here is the age value for both jonh and jonhCopy change to 25; this is because object is a reference type.
// we need to do a deep copy to avoid the referencing.
````
**Deep Copy** 
````JavaScript
const john = {
firstName: 'John',
lastName: 'Shelby',
age: 27
}
// now let's copy
const johnCopy = Object.assign({}, join);
// now let's change the value of the age
johnCopy.age = 25
// now let's print jonh and jonhCopy
console.log(jonh); // outcome: { firstName: 'John', lastName: 'Shelby', age: 27}
console.log(jonhCopy); // outcome: { firstName: 'John', lastName: 'Shelby', age: 25}
// note: this method works only in the first level of copy; this mean that if we have an object inside an object, it works only in the first level object (parent), and the object inside still reference to the value. In this case, we need to use some package libraries to achieve it.
````

