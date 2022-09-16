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
**static method**

**Object.create**
![image](https://user-images.githubusercontent.com/77439221/190049021-5c84151e-6b0f-461f-998b-33cb9df00cff.png)

**Parent and child classes: before ES6**
![image](https://user-images.githubusercontent.com/77439221/190392607-515f886d-c7f3-4a56-b697-89f4af789277.png)
![image](https://user-images.githubusercontent.com/77439221/190393482-7d551428-cc60-4597-b4c9-324acfb68f9a.png)
![image](https://user-images.githubusercontent.com/77439221/190393785-2e32c736-87d3-49c4-a971-b94cf7edf696.png)
![image](https://user-images.githubusercontent.com/77439221/190394051-ffae7f40-3eb6-4d02-b7b7-d90438dfe5ed.png)

````JavaScript
// Inheritance Between "Classes": Constructor Functions

const Person = function (firstName, birthYear) {
  this.firstName = firstName;
  this.birthYear = birthYear;
};

Person.prototype.calcAge = function () {
  console.log(2037 - this.birthYear);
};

const Student = function (firstName, birthYear, course) {
  Person.call(this, firstName, birthYear);  // this is how you inherit from parent class; we use ".call" method 
  this.course = course;
};

// Linking prototypes
Student.prototype = Object.create(Person.prototype);

Student.prototype.introduce = function () {
  console.log(`My name is ${this.firstName} and I study ${this.course}`);
};

const mike = new Student('Mike', 2020, 'Computer Science');
mike.introduce();
mike.calcAge();

console.log(mike.__proto__);
console.log(mike.__proto__.__proto__);

console.log(mike instanceof Student);
console.log(mike instanceof Person);
console.log(mike instanceof Object);

Student.prototype.constructor = Student;
console.dir(Student.prototype.constructor);

````

**Parent and child classes: in ES6**
````JavaScript
class StudentCl extends PersonCl {
  constructor(fullName, birthYear, course) {
    // Always needs to happen first!
    super(fullName, birthYear);
    this.course = course;
  }

  introduce() {
    console.log(`My name is ${this.fullName} and I study ${this.course}`);
  }

  calcAge() {
    console.log(
      `I'm ${
        2037 - this.birthYear
      } years old, but as a student I feel more like ${
        2037 - this.birthYear + 10
      }`
    );
  }
}

const martha = new StudentCl('Martha Jones', 2012, 'Computer Science');
martha.introduce();
martha.calcAge();

````

**Private class fields and methods**
````JavaScript
// by convention we use "_" in from of a field (property) or method to note that it is private (but we still can access it from outside).
// new features have been implementing for the private class fields and methods (only work on Chrome right now). In the new features, we use "#" in from of afield or method to make it private (you can't access it from outside)
// please also read about "static" field or method (note: it is similar to static in Swift)

// Encapsulation: Protected Properties and Methods
// Encapsulation: Private Class Fields and Methods

// 1) Public fields
// 2) Private fields
// 3) Public methods
// 4) Private methods
// (there is also the static version)

class Account {
  // 1) Public fields (instances)
  locale = navigator.language;

  // 2) Private fields (instances)
  #movements = [];
  #pin;

  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.#pin = pin;

    // Protected property
    // this._movements = [];
    // this.locale = navigator.language;

    console.log(`Thanks for opening an account, ${owner}`);
  }

  // 3) Public methods

  // Public interface
  getMovements() {
    return this.#movements;
  }

  deposit(val) {
    this.#movements.push(val);
    return this;
  }

  withdraw(val) {
    this.deposit(-val);
    return this;
  }

  requestLoan(val) {
    // if (this.#approveLoan(val)) {
    if (this._approveLoan(val)) {
      this.deposit(val);
      console.log(`Loan approved`);
      return this;
    }
  }

  static helper() {
    console.log('Helper');
  }

  // 4) Private methods
  // #approveLoan(val) {
  _approveLoan(val) {
    return true;
  }
}

const acc1 = new Account('Jonas', 'EUR', 1111);

// acc1._movements.push(250);
// acc1._movements.push(-140);
// acc1.approveLoan(1000);

acc1.deposit(250);
acc1.withdraw(140);
acc1.requestLoan(1000);
console.log(acc1.getMovements());
console.log(acc1);
Account.helper();

// console.log(acc1.#movements);
// console.log(acc1.#pin);
// console.log(acc1.#approveLoan(100));

````





