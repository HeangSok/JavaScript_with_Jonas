# Document Object Model (DOM)

**DOM**: Structured representation of HTML documents; allows JavaScript to access HTML elements and styles to manipulate them.

document.querySelector(".className") // select class name

document.querySelector("#idName") // select id name

console.log(document.querySelector(".className").textContent) // get only the text content and print on terminal.

document.querySelector(".className").addEventListener("clikc", function () {// do sth});

// note: for the attribute that has two words, we can't use kebab case, we use camel case instead
document.querySelector('body').style.backgroundColor = '#60b347';
