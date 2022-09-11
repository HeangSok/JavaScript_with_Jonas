# Document Object Model (DOM)

**DOM**: Structured representation of HTML documents; allows JavaScript to access HTML elements and styles to manipulate them.

document.querySelector(".className") // select class name

document.querySelector("#idName") // select id name

console.log(document.querySelector(".className").textContent) // get only the text content and print on terminal.

document.querySelector(".className").addEventListener("clikc", function () {// do sth});

// note: for the attribute that has two words, we can't use kebab case, we use camel case instead
document.querySelector('body').style.backgroundColor = '#60b347';

// to print your current viewport size:
console.log('height/width viewport:', document.documentElement.clientHeight, document.documentElement.clientWidth);

**What is the DOM**
![image](https://user-images.githubusercontent.com/77439221/188302187-c56b6f70-457a-4cba-bbb1-197db2725a16.png)

**DOM structure**
![image](https://user-images.githubusercontent.com/77439221/188302388-c36ddb85-796e-4bcc-b52e-e122d45abec6.png)

**Selecting, Creating, Deleting Elements**
````JavaScript
// selecting
const header = document.querySelector('.header');
const allSelection = document.querySelectorAll('.section'); // return a node list; this list won't change in a live time when we delete an element inside

document.getElementById('section--1') 
const allButtons = doucment.getElementsByTagName('button'); // return a 'HTML collection' list; this list different from node list. this list will change in a live time when we delete an element inside
 console.log(document.getElementsByClassName('btn')); // return a 'HTML collection' list
 
 // creating
 const message = document.createElement('div');
 message.classList.add('cookie-message');
 message.innerHTML = 'We use cookied for improved functionality and analytics. <button class="btn btn--close-cookie">Got it!<button>';
 
 header.prepend(message); // will show at the top of header element
 header.append(message); // will show at the button of header element; note: the message element can appear at one place only. to make it appears at the frist and last of the header at the same time we use:
 header.append(message.cloneNode(true));
 
 header.before(message); // add before the header element as its neighbour 
 header.after(message); // add after the header element as its neighbour 
 
 // deleting 
 document.querySelector('.btn--close-cookie').addEventListener('click', function () {
 message.remove()
 });

````

**Sytles, Attributes and Classes**
````JavaScript
// sytles
message.style.backgroundColor = '#37383d';
message.style.width = '120%';

console.log(getComputedStyle(message)) //get all the css styles and value
console.log(getComputedStyle(message).color); // get the color style value from this element
console.log(getComputedStyle(message).height); // get the height style value from this element

message.style.height = Number.parseFloat(getComputedStyle(message).height, 10) +  30 + 'px';

// suppose in css file we have: :root{--color-primary: #5ec576;}
document.documentElement.sytle.setProperty('--color-primary', 'orangered');

// attribute
const logo = document.querySelector('.nav__logo');
console.log(logo.alt);
console.log(logo.src); // return absolute path in broswer. ex: http://127.0.0.1:8080/img/logo.png
console.log(logo.getAttribute('src')); // return relative path of the file in the directory. ex: img/logo.png
console.log(logo.className); // return class name. ex: nav__logo
logo.setAttributer('newAttributeName', 'theAttributeValue'); //set a new attribute to an element. ex: <img src='img/logo.png', newAttributeName='theAttributeValue'>

logo.alt = 'Beautiful miniallist logo'; // an attribute value

// data attribute: a speciale attribute that start with the word 'data', for example, data-version-number='3.0'; it is stored in dataset object
console.log(logo.dataset.versionNumber);
// we usually use data attribute quite a lot when we work with the UI, especially when we need to store a data in the user interface (html code). 


// classes 

logo.classList.add('class1', 'class2');
logo.classList.remove('class1', 'class2');
logo.classList.toggle('class1');
logo.classList.contains('class2');

// don't use
logo.className = 'sth'; // it will overide all the classes with 'sth'

````

**Smooth Scrolling**
````JavaScript
const btnScrollTo = document.querySelector('.btn--scroll-to');
const section1 = document.querySelector('#section--1');

btnScrollTo.addEventListener('click', function (e) {
  e.preventDefault();

  const s1coords = section1.getBoundingClientRect();
  // old way; all work with old broswers
  // window.pageXOffset gives a value  of the x coordinate in pixel from the very top of the website to the very top of the viewport

  // window.scrollTo({
  //   left: s1coords.left + window.pageXOffset,
  //   top: s1coords.top + window.pageYOffset,
  //   behavior: 'smooth',
  // });

  // new way; doesn't work with old browsers
  section1.scrollIntoView({ behavior: 'smooth' });
});

````

**Type of events and event handlers**
````JavaScript
const h1 = document.querySelector('h1');

const alertH1 = function (e) {
alert('something!')
// stope the event listener
h1.removeEventListener('mouseenter', alertH1);
}

h1.addEventListenter('mouseenter', alerH1);

// or you can use old way
h1.onmouseenter = alerH1

````
![image](https://user-images.githubusercontent.com/77439221/188308637-d3806ccf-481a-4130-b03f-fc64997a702c.png)


![image](https://user-images.githubusercontent.com/77439221/189520475-8283bf36-03ba-48f0-8ad4-41b7112acdb0.png)

![image](https://user-images.githubusercontent.com/77439221/189520597-20a81a46-103b-4e7e-bc6b-146249c25c86.png)



