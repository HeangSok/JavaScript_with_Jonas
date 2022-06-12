alert() # function
console.log("hello world!") # function
console.log(typeof 23) # return Number
console.log(typeof 'apple') # return String

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

````
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

````
# Ternary operator
true ? "do this if true" : "do this if false" ;
````
**'use strict'** 👉 used for declaring strict mode in JavaScript; has to put it at the very top of the script. We should always use strict mode when working with JavaScript because some errors won't show without strict mode.
- first, strict mode forbids us to do certain things
- second, it creates visible errors in the devloper console while in other situation JavaScript would just fail silently.
