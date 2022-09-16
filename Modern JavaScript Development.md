 **Modern JavaScript develoment**
 ![image](https://user-images.githubusercontent.com/77439221/190621019-43717a7b-5bbc-46a8-8248-76d135d7095d.png)
 
 **An overview of modules**
![image](https://user-images.githubusercontent.com/77439221/190621329-f57863a0-7fad-41aa-a280-8a14f7213cbf.png)
![image](https://user-images.githubusercontent.com/77439221/190621781-fc1dd015-6e69-412a-b1f8-4497894118bd.png)
![image](https://user-images.githubusercontent.com/77439221/190622110-10d181b3-33fa-4740-8d72-13e3097ed5fd.png)
![image](https://user-images.githubusercontent.com/77439221/190622640-b3125515-4784-435e-9a43-f32a6683ba5b.png)

**Note**: Parsing means read the code without executing it 

There are two types of export is ES: **name export** and **default export**; you can use both of it together 

**Name export**: we just need to write the 'export' in front of a variable or module.
**Default export**: we default export when we want to export one thing per module. 

````JavaScript
// export example
const shippingCost = 10;

// name export: method 1
export const cart = [];
// name export: method 1
export const addToCart = function (product, quantity) {
  cart.push({ product, quantity });
  console.log(`${quantity} ${product} added to cart`);
};

const totalPrice = 237;
const totalQuantity = 23;

// name export: method 2
export { totalPrice, totalQuantity as tq };

// default export
export default function (product, quantity) {
  cart.push({ product, quantity });
  console.log(`${quantity} ${product} added to cart`);
}

````

````JavaScript 
// import example

// import 'name export'; we use {}
import { addToCart, totalPrice as price, tq } from './shoppingCart.js';

// import 'default export'
import add from './shoppingCart.js'; // since 'default export' doesn't have any name, we can give it any name; here, we use 'add'

// import 'default export' and 'name export' together
import add, { totalPrice } from './shoppingCart.js';

// import all
import * as ShoppingCart from './shoppingCart.js';

````

**Note**: starting from ES2022, we can use the await keyword outside the asynfunction when working with Module.

**Top-Level Await (ES2022)**
````JavaScript 
// use it with care because it might slow down your page
 console.log('Start fetching');
 const res = await fetch('https://jsonplaceholder.typicode.com/posts');
 const data = await res.json();
 console.log(data);
 console.log('Something');
````

**Note**: in a new project, if we want to work with npm, we need to run 'npm init'; it will create a 'package.json' file which is a file that store all the configuration for our project

**To install all dependencies in 'package.json file'**: npm i

**To install parcel as devDependencies** (not regualar dependencies): npm i parcel --save-dev

![image](https://user-images.githubusercontent.com/77439221/190656970-203b842e-1e0d-41d8-b948-aca743d69c2c.png)
![image](https://user-images.githubusercontent.com/77439221/190657410-ab703060-509e-47da-a119-89766b01c5d5.png)

![image](https://user-images.githubusercontent.com/77439221/190658543-4aec5640-3c7c-4a53-b39c-55862561eed4.png)
![image](https://user-images.githubusercontent.com/77439221/190659310-2fdcd402-1593-428b-84ee-dbf4f2b633d9.png)


![image](https://user-images.githubusercontent.com/77439221/190658543-4aec5640-3c7c-4a53-b39c-55862561eed4.png)
