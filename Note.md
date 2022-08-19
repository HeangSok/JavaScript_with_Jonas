alert() // function

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

**Destructure an Array and How to Set a Default Values**

````JavaScript

conts [x=1, y=1, z=1] = [7, 8, 9];
console.log(x, y, z) // it will print 7 8 9 on the console 

conts [x=1, y=1, z=1] = [7, 8];
console.log(x, y, z) // it will print 7 8 1 on the console 

conts [x=1, y=1, z=1] = [7];
console.log(x, y, z) // it will print 7 1 1 on the console 

````
**Destructure an Object**
````JavaScript
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavati 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // open 24 hours
      close: 24,
    },
  },

  order: function (startIndex, mainIndex) {
    return [this.starterMenu[startIndex], this.mainMenu[mainIndex]];
  },
};

// to destructure an object, the new variables name must be the same as the object's properties name; and it's enclosed in {}
const { name, openingHours, categories } = restaurant;
console.log(name, openingHours, categories);

// if you want a to destructure an object with new variables that are different from the object's properties
const {
  name: restaurantName,
  openingHours: hours,
  categories: tags,
} = restaurant;

console.log(restaurantName, hours, tags);

// set defaul value
const { menu = [7, 8], starterMenu: starters = [8, 9] } = restaurant;
console.log(menu, starters);

````
**Mutating Variables**

````JavaScript

let a = 111;
let b = 999;
const obj = { a: 23, b: 7, c: 14 };
({ a, b } = obj); // need to wrape this line of code in parentheses (), or you will get an error
console.log(a, b);
````

**Destructure a Nested Object**
````JavaScript
const {
  fri: { open, close },
} = restaurant.openingHours;
console.log(open, close);

// or we can set other names for open, an d close variables
const {
  fri: { open: o, close: c },
} = restaurant.openingHours;
console.log(o, c);


````

**Passing Object as Parameter**
````JavaScript
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavati 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // open 24 hours
      close: 24,
    },
  },

  order: function (startIndex, mainIndex) {
    return [this.starterMenu[startIndex], this.mainMenu[mainIndex]];
  },

  orderDelivery: function ({
    starterIndex = 1,
    mainIndex = 0,
    time = '20:00',
    address,
  }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
    );
  },
};

restaurant.orderDelivery({
  time: '22:30',
  address: 'Via del sole, 21',
  mainIndex: 2,
  starterIndex: 2,
});
// result: Order received! Garlic Bread and Risotto will be delivered to Via del sole, 21 at 22:30

````
👉 **Iterables**: arrays, strings, maps, sets, Not Objects.

**Ternary Operator**:
````JavaScript
let hungry = true
const eatingLunch = hungry ? "Yes" : "No"
````
**The Nullish coalescing operator**
````JavaScript
// it is similar to Nil-coalescing in Swift
const eatingLunch = hungry ?? "You see this message becuase 'hungry' is 'Nullish'"
console.log(eatingLunch)
````

**Logic-Assignment Operator**

````JavaScript
const rest1 = {
name: 'Capri',
numGuests: 0,
};

const rest2 = {
name: 'La Pizza',
owner: 'Giovanni Rossi',
};

// OR Assignment Operator
// rest1.numbGuests = rest1.numGuests || 10;
// rest2.numGuests = rest2.numGuests || 10;
rest1.numGuests ||= 10;
rest2.numGuests ||= 10;

// Nullish Assignment Operator (null or undefined)
rest1.numGuests ??= 10;
rest2.numGuests ??= 10;

// AND Assignment Operator 
rest1.owner &&= 'ANONYMOUS'; // if rest1 doesn't have 'owner', it will create one and set the value to 'undefined' 
rest2.owner &&= 'ANONYMOUS'; // if rest2.owner has value, it changes to anonymous

````

**Spread Operator (...)**
````JavaScript
// We use the Spread Operator to build a "new array" or to "pass multiple values into a function"
// The Spread Operator will loop through the elements in the array, and take it out one by one.
const arr = [7, 8, 9];
const newArr = [1, 2, ...arr];
console.log(newArr); // result: [1, 2, 7, 8, 9]
console.log(...newArr); // result: 1 2 7 8 9
console.log(newArr[3]);

// without the Spread Operator
const arr = [7, 8, 9];
const newArr = [1, 2, arr]
console.log(newArr); // result: [1, 2, [7, 8, 9]]

````
**Rest Operator**
````JavaScript
// The rest operator uses the same syntax like the "Spread Operator", but we use it to collect elements, then put it into an array. 
// In another word, we use "Spread Operator" to unpack an array, while use "Rest Opearator" to pack an array

// We normally use "Spread" on the Right side of =
const arr = [1, 2, ...[3, 4]]; // it equals: const arr =  [1, 2, 3, 4]

// We normally use "Rest" on the Left side of =
const [a, b, ...others] = [1, 2, 3, 4, 5] // Note: Rest Operator's element must be the last element 
console.log(a, b, others) // others will equal to [3, 4, 5]

// use Rest Operator as the argument
const add = function (...numbers) {
let sum = 0
for (let  i = 0; i < numbers.length; i++) {
sum += numbers[i];
}
console.log(sum);
}

add(2, 3) // result: 5
add(2, 3, 4, 5) // result: 14
add(2, 3, 4, 5, 6)

const x = [1, 2, 3]
add(...x) // reslult: 6

````

**Enhance Object Literal**
````JavaScript
// Usage 1
// ES6 enhanced object literals
const openingHours = {
mon: {
open: 9,
close: 17,
},
tue: {
open: 9,
close: 17,
}
}

const restaurant = {
name: 'Italino',
// Enhance object liters
openingHours, // note: we use the same name as the object that we want to enhance.
owner: 'Jack'

// Usage 2
// we can also write a method of an object like below from ES6
order(foodName, quantity){
console.log(`Your order is: ${foodName} => ${quantity}`)
}
// note: this order method is the same as order: function (foodName, quantity) {...}

}

// Usage 3

const weekdays = ['mon', 'tue', 'wed', 'thu', 'fri']
// if we want to get the element in the weekdays and use it as the key inside an object, we can:
const openingHours = {
[weekdays[0]]: {
open: 9,
close: 17,
}, // it is the same as mon: { open: 9, close: 17,}

[weekdays[1]]: {
open: 9,
close: 17, 
}, // it is the same as tue: { open: 9, close: 17,}

}

````
**Optional Chaining (?.)**
````JavaScript
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavati 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // open 24 hours
      close: 24,
    },
  },

  order: function (startIndex, mainIndex) {
    return [this.starterMenu[startIndex], this.mainMenu[mainIndex]];
  },
}

// for objects
console.log(restaurant.openingHours?.mon?.open) // it is the same as => if (restaurant.openingHours && restaurant.openingHours.mon) {console.log(restaurant.openingHours.mon.open)}

//  for methods
console.log(restaurant.order?.(0, 1) ?? 'Mehod does not exist')

// for arrays
const users = [{name: 'Jonh', email: 'John@Shelby.io'}]
console.log(users[0]?.name ?? "User array empty") // with optional, if the array doesn't have values, it gives you "undefined"

````

**Looping Objects: Object Keys, Values, and Entries (Entries means keys + values)**
````JavaScript
// to get all the keys of an object in a list

const trimesterOne = {course: 'Python', teacherName: 'John'}
const objectKeys = Object.keys(trimesterOne);

console.log(objectKeys); // ["course", "teacherName"]

// to get all the values from an object

const values = Object.values(trimesterOne);
console.log(values); // ["Python", "John"]

// to get all keys ant values of an object at the same time

const entries = Ojbect.entries(timesterOne);
console.log(entries); // > [Array(1), Array(2)]

for (const [key, value] of entries) {
console.log(`key:${key}, value:${value}`)
}

````

**Set**
````JavaScript
// set was introduced in ES6; a set is collection of unique value, it can never have a duplicate value

const ordersSet = new Set(['Pasta', 'Pizza']) // we need an iterable inside the set function
console.log(ordersSet.size); // it will prints 2
console.log(ordersSet.has("Pizza")); // it will return true
console.log(ordersSet.has("apple")); // it will return false
ordersSet.add('Bread');
ordersSet.delete('Pizza'); // it will delete "Pizza"
ordersSet.delete('apple'); // since "apple" is not on the list, it will do nothing
ordersSet.clear(); // delete all the elements in the set

// let's try to delete the duplicate values of an array using "set"
const staff = ['Waiter', 'Chef', 'Waiter', 'Manager', 'Chef', 'Waiter'];
const staffUnique = new Set(staff);
console.log(staffUnique);

// let's convert the set to an array
const arrayOfUniqueStaff = [...staffUnique]
console.log(arrayOfUniqueStaff)

````

**Map** 
````JavaScript
// Map is a new data structure in JavaScript; we use it to map values to keys

const restaurant = new Map();
// the "set" method allows you to add a new element to the map data structure  
restaurant.set('restaurantName', 'Italiano') // the first argument is the key; the second is the value


restaurant.set('categories', ['apple', 'banana']).set('open', 11).set('close', 23).set(true, 'We are open :D').set(false, 'We are closed :(');

console.log(restaurant.get('restaurantName')) // Italiano
console.log(restaurant.get(true)) // We are open :D

const time = 8
console.log(restaurant.get(time > rest.get('open') && time < rest.get('close'))); // We are closed :(

console.log(restaurant.has('categories')); // return a boolean
restaurant.delete('categories'); // delete the key
restaurant.delete('sth'); // since 'sth' is not exist, it will do nothing
restaurant.clear(); // delete all elements
console.log(restaurant.size); // print the size of the map

````

**More on Map**
````JavaScript
// let's create a map data structure

const question = new Map([
['Question1', 'What is the best programming language in the world?'], // the first index is key; the second is value
[1, 'C++'],
[2, 'JavaScript'],
[3, 'Python'],
['correct', 3],
[true, 'Correct 🎉'],
[false, 'Try again!'],
]);

console.log(question);

// convert object to map
console.log(Object.entries(openingHours));
const openingHoursMap = new Map(Object.entries(openingHours));

console.log(hoursMap);

// let's work with iteration
console.log(questrion.get('question'));

for (const [key, value] of question) {
if (typeof key === 'number') console.log(`Answer ${key}: ${value}`);
}

const answer = 3;
console.log(question.get(question.get('correct') === answer));

// conver a map to an array
console.log([...question]); // make arrays in an arrays; ex: [Array(1), Array(2), Array(3)]
console.log([...question.keys()]); // make an array of keys
console.log([...question.values()]); // make an array of values

````
**Data Structures**
![image](https://user-images.githubusercontent.com/77439221/185686261-c70181c1-800e-4e3c-b76d-5160fd3083a2.png)

**Working with String Part 1**
````JavaScript
const airline = 'TAP Air Portugal';
const plane = 'A320';

console.log(plane[0]) // get the position of the character of index 0

console.log(airline.length) // get the length of the string

console.log(airline.indexOf('r')); // get the index of the first 'r'
console.log(airline.lastIndexOf('r')); // get the index of the last 'r'
console.log(airline.indexOf('portugal'));

// slicing 
console.log(airline.slice(4)); // it will return "Air Portugal"
console.log(airline.slice(4, 7)); // it returns "Air"; note: it will slice from index 4 to 6, but not 7

console.log(airline.slice(0, airline.indexOf(' '))); // return "TAP"
console.log(airline.slice(-5));

````

**Working with String Part 2**
````JavaScript
const airline = 'TAP Air Portugal';

console.log(airline.toLowerCase());
console.log(airline.toUpperCase());

// to capitalise the first letter
const passenger = 'joHN';
const passengerLower = passenger.toLowerCase();
const passengerCorrect = passengerLower[0].toUpperCase() + passengerLower.slice(1);
console.log(passengerCorrect);

// Comparing emails
const email = 'hello@world.io';
const loginEmail = '   Hello@world.Io \n';

const lowerEmail = loginEmail.toLowerCase();
const trimmedEmail = lowerEmail.trim(); 

// or we can:

const normalizedEmail = loginEmail.toLowerCase().trim();
console.log(normalizedEmail);

// replace parts of string

const priceUS = '288,97US';
const priceAUD = priceUS.replace('US', 'AUD').replace(',', '.'); // note: .replace() will replace only the first occurance.
console.log(priceAUD)

// replaceAll()
conts announcement = 'All passengers come to boarding door 23. Boarding door 23!';
console.log(announcdemnt.replaceAll('door', 'gate'));

// using regex to replace all 
console.log(announcdemnt.replace(/door/g, 'gate')); // need to write door in between of // to work with regular expression;g means global

// booleans
const plane = 'A320neo';
console.log(plane.includes('A320')); // true
console.log(plane.startsWith('Air')); // false
console.log(plane.endsWith('sth')); // false

// split

console.log('a+very+nice+day'.split('+')); // will return ['a', 'very', 'nice', 'day']
console.log('john shelby'.split(' ')); // will return ['john', 'shelby']

const [firstName, lastName] = 'Jonas Schmedtmann'.split(' ');

// join
const newName = ['Mr.', firstName, lastName.toUppercase()].join(' ');
console.log(newName); // returns: Mr. Jonas SCHMEDTMANN

// to capitalise each word

const capitalizedName = function(name) {
consts names = name.split(' ');
const namesCapitalized = [];

for (const n of names) {
namesCapitalized.push(n[0].toUpperCase() + n.slice(1));
// or we can:
// namesCapitalized.push(n.replace(n[0], n[0].toUpperCase());
}
console.log(nameCapitalizdd.join(' '));
};

capitalizedName('jonh smith'); // returns: John Smith
capitalizedName('jonas schmedtmann'); // returns: Jonas Schemdtmann

// padding string

const message = 'Go to gate 23!'
console.log(message.padStart(20, '+')); // returns: ++++++Go to gate 23!; the first argument means we want the whole length to be 20 characters; the second means add the + charactor to the start of the message

console.log(message.padStart(20, '+').padEnd(30,'+')); // returns: ++++++Go to gate 23!++++++++++; the total lenght is 30 characters.

// real case example:  we can use padding to hide part of your credit card number
const maskCreditcard = function (number) {
const str = String(number);
const lastFourDigits = str.slice(-4);
return lastFourDigits.padStart(str.length, '*');
}

console.log(maskCreditcard(421343243213441)) // returns: ***********3441

// repeat
const message = 'Bad weather...All planes Delayed...🛩';
conole.log(message.repeat(5)); // the message will be repeated 5 times, one after another


const planeInLine = function (n) {
console.log(`There are ${n} planes in line ${'🛩'.repeat(n)}`);
};

planesInLine(3); // returns: There are 3 planes in line 🛩🛩🛩

````

 



