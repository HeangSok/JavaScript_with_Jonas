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

 **More about Function**
 ````JavaScript
 // Default Parameters
const bookings = [];

const createBooking = function (
  flightNum,
  numPassengers = 1,
  price = 199 * numPassengers
) {
  // this is how we set default parameter in ES5
  // numPassengers = numPassengers || 1;
  // price = price || 199;

  const booking = {
    flightNum,
    numPassengers,
    price,
  };
  console.log(booking);
  bookings.push(booking);
};

createBooking('LH123');
createBooking('LH123', 2, 800);
createBooking('LH123', 2);
createBooking('LH123', 5);
 
 ````
 
 **How Passing Arguments Works: Values vs. Reference**
 ````JavaScript
 // be careful when you passing object as an argument becasue it is not a primitive type, yet a reference type.
 // please: watch this lecture: https://www.udemy.com/course/the-complete-javascript-course/learn/lecture/22648645#notes
 
const flight = 'LH234';
const jonas = {
  name: 'Jonas Schmedtmann',
  passport: 24739479284,
};

const checkIn = function (flightNum, passenger) {
  flightNum = 'LH999'; // this line won't change the value of the "flight" variable outside the function
  passenger.name = 'Mr. ' + passenger.name; // this line will change the value of "jonas" object outside the function

  if (passenger.passport === 24739479284) {
    alert('Checked in');
  } else {
    alert('Wrong passport!');
  }
};

// checkIn(flight, jonas);
// console.log(flight);
// console.log(jonas); // return: { name: 'Mr. Jonas Schmedtmann', passport: 24739479284 }; it added "Mr." to "Jonas Schmedtmann"

// Is the same as doing...
// const flightNum = flight;
// const passenger = jonas;

const newPassport = function (person) {
  person.passport = Math.trunc(Math.random() * 100000000000);
};

newPassport(jonas);
checkIn(flight, jonas);
 
 ````
 **First-Class and Higher-Order Functions**
 ![image](https://user-images.githubusercontent.com/77439221/185758907-e3f3b4a5-9fea-4093-950c-2d193dc8ce07.png)

**Functions Accepting Callback Functions**
````JavaScript

// let's create a function that omits all spaces of a string, then turns it to lowercase
const oneWord = function (str) {return str.replace(/ /g, '').toLowerCase();};

// let's create a function that that convert the frist word of a to uppercase
const upperFirstWord = function (str) {
const [first, ...others] = str.split(' ');
return [first.toUpperCase(), ...others].join(' ');
};

// higher-order function: a function either takes function as an argument or return a function
const transformer = function (str, func) {
console.log(`Original string: ${str}`);
console.log(`Transformed string: ${func(str)}`);
console.log(`Transformed by: ${fn.name} function`);
};

transformer('JavaScript is the best!', upperFirstWord);
transformer('JavaScript is the best', oneWord);

````

**Functions returning functions**
````JavaScript
const greet = function (greeting) {
return function (name) {
console.log(`${greeting} ${name}`);
};
};
// let's call the function that returns a function
greet('Hello')('John'); // will return: Hello John

// or you can store it in a variable; then call the variable
const greeterHey = greet('Hey');
greeterHey("John"); // returns: Hey John
greeterHey("Smith"); // returns: Hey Smith

// Challenge: rewrite the function above using arrow function syntax
const greetArr = greeting => name => console.log(`${greeting} ${name}`);

greetArr('Hi')('Jack'); // 

````
**The call and apply Methods**
````JavaScript
const lufthansa = {
  airline: 'Lufthansa',
  iataCode: 'LH',
  bookings: [],
  // book: function() {}
  book(flightNum, name) {
    console.log(
      `${name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`
    );
    this.bookings.push({ flight: `${this.iataCode}${flightNum}`, name });
  },
};

lufthansa.book(239, 'Jonas Schmedtmann');
lufthansa.book(635, 'John Smith');

const eurowings = {
  airline: 'Eurowings',
  iataCode: 'EW',
  bookings: [],
};

// let's copy the function into a variable so that we can reuse it 
const book = lufthansa.book;

// Does NOT work: because the 'this' keyword inside the function now doesn't point 'lufthansa'
// book(23, 'Sarah Williams');


// Call method: we use call method to manually point 'this' keyword to the object that we want to work with; in this case 'eurowings' object.
book.call(eurowings, 23, 'Sarah Williams'); // the first argument is the object we want to work with; then we just pass the rest of the argument in its order 
console.log(eurowings);

book.call(lufthansa, 239, 'Mary Cooper');
console.log(lufthansa);

const swiss = {
  airline: 'Swiss Air Lines',
  iataCode: 'LX',
  bookings: [],
};

book.call(swiss, 583, 'Mary Cooper');

// Apply method: 'apply' and 'call' are similar; but 'apply' take the array as the second argument.
const flightData = [583, 'George Cooper'];
book.apply(swiss, flightData);
console.log(swiss);

book.call(swiss, ...flightData);

// Bind method: just like the call method, bind allows us to manually set the 'this keyword' for any function call
// the difference is that bind doesn't call the function immediately; it returns a new function where the 'this' keyword is bound

const bookEW = book.bind(eurowings); // now we point the 'this' keyword in book to 'eurowings'; but we are not calling it yet. with bind, it just create a new function and save to bookEW

bookEW(23, 'Steven Williams'); // now let's call the function and pass the arguments

// we can also partially/fully set the predefined values of the arguments; not that it is not the same as when you set the default value which you can set to new values (or if you don't give any value it will use the defualt value). The predefined values is fixed and are always used.

// let's set the predefined values
const bookEW = book.bind(eurowings, 23); // this '23' will be always used

bookEW('Steven Williams'); // we can't set a new number here to replace 23; 23 will be always used in bookEW


// Bind method with Event Listeners
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this);

  this.planes++;
  console.log(this.planes);
};
// lufthansa.buyPlane();

document
  .querySelector('.buy')
  .addEventListener('click', lufthansa.buyPlane.bind(lufthansa)); 
  // the 'this' keyword here point to the element that the Event Listeners attached to, so we need to set it manually to the object that we want to work with
  // we use bind method here because call method will call the function immediately which we don't want to happen here



// Partial application
const addTax = (rate, value) => value + value * rate;
console.log(addTax(0.1, 200));

// we point to null because the function above doesn't use 'this' keyword; we want to set the 'rate' argument to be always 0.23 that is why we use bind method. note it is not the same as setting the default value.
const addVAT = addTax.bind(null, 0.23); 
//the line above means: addVAT = value => value + value * 0.23;

console.log(addVAT(100));  // we can't write: console.log(addVAT2(0.5, 100)); this is because the rate parameter is always 0.23 now. if you give 2 parameters here, it will take only the first one.
console.log(addVAT(23));

````
**Immediately Invoked Function Expression (IIFE)**
````JavaScript
// sometimes, in JavaScript, we need a function that executed only once and never again. This function will be disappear right after it is called once
// we usually use IIFE with Asyn and Wait

(function () {console.log('This will never run again');})();

(() => console.log('This will ALSO never run again');)();

````

**Closures**
![image](https://user-images.githubusercontent.com/77439221/185763949-1ad9586e-a9f3-4cf1-8319-bfb95ce8d212.png)


**Array methods**
````JavaScript

// slice: it won't mutate the original array

let arr = ['a', 'b', 'c', 'd', 'e'];

console.log(arr.slice(2)); // returns: ['c', 'd', 'e']
console.log(arr.slice(2, 4)); // returns: ['c', 'd']
console.log(arr.slice(2, -1)); // returns: ['c', 'd']

// splice: it will mutate the original array

// the code below will return: ['c', 'd']
console.log(arr.splice(2, 2)); // the first arguement is the start index; the 2nd is the numbers of the elements that you want to take out

console.log(arr) // returns: ['a', 'b', 'e']; this is because we used ".splice" to take 2 elements out of the array

// reverse
console.log(arr.revere()); // returns: ['e', 'd', 'c', 'b', 'a']

// concat: not mutate the original array

let arr2 = ['f', 'g'];
const letters = arr.concat(arr2);
console.log(letters); // returns: ['a', 'b', 'c', 'd', 'e', 'f', 'g']

// join: join an array to a string
console.log(letters.join(' ')); // returns: a b c d e f g

````

**'at' method**
````JavaScript
const arr = [1, 2, 3, 4, 5];
console.log(arr[0]); // returns: 1
console.log(arr.at(0)); // returns: 1

// to get the last element
console.log(arr[-1]); // returns: undefined
console.log(arr.at(-1)); // returns: 5
// or you can use slice to get the last element
console.log(arr.slice(-1)); // returns: 5

````
**forEach**
````JavaScript
// working with array
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
// note: we use a callback function inside forEach method; each element of the array will pass to the function at each iteration
// the first argument is the element of the array; second is the index number; third is the entire array.
movements.forEach(function (movement, indexNumber, entireArray) { 
if (movement > 0) {
console.log(`Movement ${indexNumber + 1}: You deposited ${movement}`);
} else {
console.log(`Movement ${indexNumber + 1}: You withdrew ${movement}`);
}

}); 

// working with map
const currencies = new Map([
  ['USD', 'United States dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound sterling'],
]);

currencies.forEach(function (value, key, map) {
  console.log(`${key}: ${value} ; ${map}`);
});
// iteration1: USD: United States dollar ; [object Map]
// iteration2: EUR: Euro ; [object Map]
// iteration3: GBP: Pound sterling ; [object Map]


// working with set

const currenciesUnique = new Set(['USD', 'GBP', 'EUR']);

// Note: set doesn't have index number that is why we use '_' for this argument; by convention, '_' is used for the variable/parameter that we don't need 
currenciesUnique.forEach(function(value, _, set) {
console.log(`${value}; ${set}`)
});

// iteration1: USD; [object Set]
// iteration2: GBP; [object Set]
// iteration3: EUR; [object Set]


````

![image](https://user-images.githubusercontent.com/77439221/187010424-92552ae4-9859-4ae7-b53d-62255ac7e7e9.png)

**The map method**
````JavaScript
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const eurToUsd = 1.1; // coversion rate

const newArray = movements.map(function (mov) {
  return mov * eurToUsd;
});

console.log(newArray);
````

**The filter method**
````JavaScript
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const deposits = movements.filter(function (mov) {
  return mov > 0;
});
console.log(deposits); // [200, 450, 3000, 70, 1300]

const withdrawals = movements.filter(mov => mov < 0);
console.log(withdrawals); // [-400, -650, -130]
````

**The reduce method**
````JavaScript
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const balance = movements.reduce(function (
  accumulator,
  currentElement,
  index,
  entireArr
) {
  return accumulator + currentElement;
},
0); // the first parameter for the '.reduce' method is a callback function; the second is the 'intial value' of the accumulator

console.log(balance); // 3840

// to get a maximum value
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

const max = movements.reduce((accumulator, currentElement) => {if (accumulator > currentElement) return accumulator; else return currentElement;}, movements[0]);

console.log(max); // 3000

````
**The find method**
````JavaScript
// the difference between find and filter is: - filter returns a new array that meet the condition while find returns only the first element that meet the condition

const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
const firstWithdrawal = movements.find(mov => mov < 0);
console.log(firstWithdrawal); // -400

````

**The findIndex method**
````JavaScript
// findIndex returns the index of the first found element
// also check .indexOf()

````

**The includes, some, every methods**
````JavaScript
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

// includes uses exact value 
console.log(movements.includes(-130)) // true

// some uses callback function and condition
console.log(movements.some(mov => mov > 1500)) // true
console.log(movements.some(mov => mov > 5000)) // false

// every method returns true only if all the elements in the array satifies the condition that we pass in
console.log(moements.every(mov => mov > 0)); // false

````
**The flat method**
````JavaScript

// level one of nested array
const arr = [[1, 2, 3], [4, 5 ,6], 7, 8];
console.log(arr.flat()); // [1, 2, 3, 4, 5, 6, 7, 8]

// levle two of nested array
const arrDeep = [[[1, 2], 3], [4, [5, 6]], 7, 8];
console.log(arrDeep.flat(2)); // [1, 2, 3, 4, 5, 6, 7, 8]

// also check the flatMap method

````
**The sort method**
````JavaScript
// String
const strArr1 = ['a', 'c', 'z', 'f'];
// sort ascending order with string
console.log(strArr1.sort());
// sort descending order with string
console.log(strArr1.sort((a, b) => (a > b ? -1 : 1)));
// sort descending order with string
console.log(strArr1.sort().reverse());

// Number
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];
console.log(movements.sort()); // will give you a wrong answer

// return something < 0 means (keep order of the element inside the array when sorting)
// return something > 0 means (switch order of the element inside the array when sorting)

// Ascending
// movements.sort((a, b) => {if (a > b) return 1; if (a < b) return -1;});
// console.log(movements);

movements.sort((a, b) => a - b);
console.log(movements);

// Descending
// movements.sort((a, b) => {
//   if (a > b) return -1;
//   if (a < b) return 1;
// });
movements.sort((a, b) => b - a);
console.log(movements);

````



