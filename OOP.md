![image](https://user-images.githubusercontent.com/77439221/189522087-ec1f3ced-6505-45ef-a410-b7da68bdd86c.png)
![image](https://user-images.githubusercontent.com/77439221/189522144-129d491e-6203-428a-b51f-109dae541cb0.png)
![image](https://user-images.githubusercontent.com/77439221/189522206-740b2497-3636-4026-9b8f-e34c7dfea9e5.png)
![image](https://user-images.githubusercontent.com/77439221/189522254-30497b64-f45a-4b36-9c70-43939f02dba3.png)
![image](https://user-images.githubusercontent.com/77439221/189522330-3c6d4117-8f95-4f30-b32a-4b2826546af5.png)
![image](https://user-images.githubusercontent.com/77439221/189522441-d0a5d0cb-c842-4679-bf2e-882dd041737b.png)
![image](https://user-images.githubusercontent.com/77439221/189522475-8f4439fa-b565-4cef-bb72-b7c5f320a768.png)
![image](https://user-images.githubusercontent.com/77439221/189522653-9a817731-c3e8-4116-a07e-895f6a25fcc1.png)
![image](https://user-images.githubusercontent.com/77439221/189522706-36fee5d1-7f35-454f-a7f6-a2800e53231a.png)
![image](https://user-images.githubusercontent.com/77439221/189525367-616d7c25-b145-4abe-80c9-47db7f7bb98a.png)
![image](https://user-images.githubusercontent.com/77439221/189525471-219a7709-40d1-4577-87c1-754bdfd2d698.png)


**class expression vs class declaration**
````JavaScript

// 1. Classes are NOT hoisted
// 2. Classes are first-class citizes
// 3. Classes are executed in strict mode (all the code in the class will be executed in strict mode)

// class expression
const PersonCl = class {//some codes}

// class declaration
class PersonCl {
   constructor(firstName, birthYear) {
   this.firsName = firstName;
   this.birthYear = birthYear;
   }
   
   // Methodes will be added to .prototype property
   calcAge() {
   console.log(2037 - this.birithYear);
   }
   
   greet() {
   console.log(`Hey ${this.first.Name}`);
   }
}

const jessica = new PersonCl('Jessica', 1996);
console.log(jessica);
jessica.calcAge();

console.log(jessica.__proto__ === PersonCl.prototype); // return: true.

````
**getter and setter**
````JavaScript
// getter and setter can exist both object and class

// getter and setter in an object
const account = {
owner: 'John',
movements:[200, 530, 120, 300],

get latest() { // note: latest is a property now, not a method
return this.movements.slice(-1).pop();
},

set latest(move) { // note: latest is a property now, not a method
this.movennts.push(move);
}, 
};

console.log(account.latest);
account.latest = 50; // note: sice latest is a property, we set a new value to it like this, not: account.latest(50)
console.log(account.movements);


````
