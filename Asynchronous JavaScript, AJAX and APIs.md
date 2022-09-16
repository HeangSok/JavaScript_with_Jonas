**Synchronous code**

![image](https://user-images.githubusercontent.com/77439221/190556665-cb933339-ad4c-4eda-b796-520dc3d67b81.png)

**Asynchronous code**

![image](https://user-images.githubusercontent.com/77439221/190556911-1d800bdd-555c-4a10-bcf8-ddc74ef04073.png)

![image](https://user-images.githubusercontent.com/77439221/190557081-f0d7e130-ec9a-4522-9447-50e19460d2b8.png)

**AJAX**
![image](https://user-images.githubusercontent.com/77439221/190557249-3890b88d-0fdc-48a9-83a8-cc15a5d23825.png)

![image](https://user-images.githubusercontent.com/77439221/190557621-3b17ee42-95ee-45af-a5ac-abb6bff31548.png)

**http request and respond**
![image](https://user-images.githubusercontent.com/77439221/190566113-cc3db1be-0fdd-4463-85d6-5c0b68593f80.png)

**Promises**
![image](https://user-images.githubusercontent.com/77439221/190567654-46e79a06-4e36-4c2f-a660-30fca5294604.png)

![image](https://user-images.githubusercontent.com/77439221/190567906-429dd95e-ac3d-4cdb-952b-49dd866f2a3e.png)

````JavaScript
// Consuming Promises
// Chaining Promises
// Handling Rejected Promises
// Throwing Errors Manually

 const getCountryData = function (country) {
 // note: the fetch api always return a promise; after a promise we can use 'then' for next step; 
 // note: 'then' can accept two fall back function. The first fall back function will handle when the promise is successful fulfilled. The second fall back function will handle all the errors, for example, when we can't fetch the data from the api.
   fetch(`https://restcountries.eu/rest/v2/name/${country}`)
     .then(function (response) {
       console.log(response);
       return response.json();
     })
     .then(function (data) {
       console.log(data);
       renderCountry(data[0]);
     });
 };

 const getCountryData = function (country) {
   // Country 1
   fetch(`https://restcountries.eu/rest/v2/name/${country}`)
     .then(response => {
       console.log(response);
      // Throwing error manaully; this new message will send to .catch
       if (!response.ok)
         throw new Error(`Country not found (${response.status})`);

       return response.json();
     })
     .then(data => {
       renderCountry(data[0]);
       // const neighbour = data[0].borders[0];
       const neighbour = 'dfsdfdef';

       if (!neighbour) return;

       // Country 2
       return fetch(`https://restcountries.eu/rest/v2/alpha/${neighbour}`);
     })
     .then(response => {
       if (!response.ok)
         throw new Error(`Country not found (${response.status})`);

       return response.json();
     })
     .then(data => renderCountry(data, 'neighbour'))
     // instead of using the second fall back function at each of 'then' in promise chaining, we can just use .catch 
     .catch(err => {
       console.error(`${err} 💥💥💥`);
       renderError(`Something went wrong 💥💥 ${err.message}. Try again!`);
     })
     // .fianlly is a method that will eventually executed no matter what
     .finally(() => {
       countriesContainer.style.opacity = 1;
     });
 };

const getCountryData = function (country) {
  // Country 1
  getJSON(
    `https://restcountries.eu/rest/v2/name/${country}`,
    'Country not found'
  )
    .then(data => {
      renderCountry(data[0]);
      const neighbour = data[0].borders[0];

      if (!neighbour) throw new Error('No neighbour found!');

      // Country 2
      return getJSON(
        `https://restcountries.eu/rest/v2/alpha/${neighbour}`,
        'Country not found'
      );
    })

    .then(data => renderCountry(data, 'neighbour'))
    .catch(err => {
      console.error(`${err} 💥💥💥`);
      renderError(`Something went wrong 💥💥 ${err.message}. Try again!`);
    })
    .finally(() => {
      countriesContainer.style.opacity = 1;
    });
};

btn.addEventListener('click', function () {
  getCountryData('portugal');
});

getCountryData('australia');

````
![image](https://user-images.githubusercontent.com/77439221/190578137-c5038110-8fe6-4f47-9298-37f9015d6771.png)
![image](https://user-images.githubusercontent.com/77439221/190579743-fa162c61-8c9d-4e84-aa48-bdef5deef7c6.png)
![image](https://user-images.githubusercontent.com/77439221/190579781-ded89ef2-b989-4f87-8a29-4a1c4b09abbe.png)
![image](https://user-images.githubusercontent.com/77439221/190579865-64f80ac5-24c7-4959-9fd0-e341b824797b.png)
![image](https://user-images.githubusercontent.com/77439221/190579905-e9eecde7-54ce-4dd2-abbe-c8d9c5461473.png)


**Building a simple Promise**
````JavaSript
// note: the Promise constructor's call back function has two argument one is resolve (means that the promise is fulfilled); one is reject (means that the promise is rejected; use it to tell what error it is in catch)
const lotteryPromise = new Promise(function (resolve, reject) {
  console.log('Lotter draw is happening 🔮');
  setTimeout(function () {
    if (Math.random() >= 0.5) {
      resolve('You WIN 💰');
    } else {
      reject(new Error('You lost your money 💩'));
    }
  }, 2000);
});

lotteryPromise.then(res => console.log(res)).catch(err => console.error(err));

// Promisifying setTimeout
const wait = function (seconds) {
  return new Promise(function (resolve) {
    setTimeout(resolve, seconds * 1000);
  });
};

wait(1)
  .then(() => {
    console.log('1 second passed');
    return wait(1);
  })
  .then(() => {
    console.log('2 second passed');
    return wait(1);
  })
  .then(() => {
    console.log('3 second passed');
    return wait(1);
  })
  .then(() => console.log('4 second passed'));

Promise.resolve('abc').then(x => console.log(x));
Promise.reject(new Error('Problem!')).catch(x => console.error(x));
````

**Asyn and Await**

````JavaScript
// Asyn and await is a syntactic sugar for consuming promise. 
const whereAmI = async function () {
  try {
    // Geolocation
    const pos = await getPosition();
    const { latitude: lat, longitude: lng } = pos.coords;

    // Reverse geocoding
    const resGeo = await fetch(`https://geocode.xyz/${lat},${lng}?geoit=json`);
    if (!resGeo.ok) throw new Error('Problem getting location data');

    const dataGeo = await resGeo.json();
    console.log(dataGeo);

    // Country data
    const res = await fetch(
      `https://restcountries.eu/rest/v2/name/${dataGeo.country}`
    );
    
    if (!res.ok) throw new Error('Problem getting country');

    const data = await res.json();
    console.log(data);
    renderCountry(data[0]);
  } catch (err) {
    console.error(`${err} 💥`);
    renderError(`💥 ${err.message}`);
  }
};
whereAmI();

````
**handle with returning values from asyn functions**

````JavaScript
// note: an asyn function always return a promise 
const getPosition = function () {
  return new Promise(function (resolve, reject) {
    navigator.geolocation.getCurrentPosition(resolve, reject);
  });
};

const whereAmI = async function () {
  try {
    // Geolocation
    const pos = await getPosition();
    const { latitude: lat, longitude: lng } = pos.coords;

    // Reverse geocoding
    const resGeo = await fetch(`https://geocode.xyz/${lat},${lng}?geoit=json`);
    if (!resGeo.ok) throw new Error('Problem getting location data');
    const dataGeo = await resGeo.json();

    // Country data
    const res = await fetch(
      `https://restcountries.eu/rest/v2/name/${dataGeo.country}`
    );
    if (!resGeo.ok) throw new Error('Problem getting country');
    const data = await res.json();
    renderCountry(data[0]);

    return `You are in ${dataGeo.city}, ${dataGeo.country}`;
  } catch (err) {
    console.error(`${err} 💥`);
    renderError(`💥 ${err.message}`);

    // Reject promise returned from async function
    throw err;
  }
};


console.log('1: Will get location');

// method 1: using .then to handle the promise that return from the asyn function
 whereAmI()
   .then(city => console.log(`2: ${city}`))
   .catch(err => console.error(`2: ${err.message} 💥`))
   .finally(() => console.log('3: Finished getting location'));
   
// method 2: using IIFE (Immediately Invoked Function Expression)
(async function () {
  try {
    const city = await whereAmI();
    console.log(`2: ${city}`);
  } catch (err) {
    console.error(`2: ${err.message} 💥`);
  }
  console.log('3: Finished getting location');
})();

````

**Running promise in parallel**
```JavaScript
const get3Countries = async function (c1, c2, c3) {
  try {
    // const [data1] = await getJSON(
    //   `https://restcountries.eu/rest/v2/name/${c1}`
    // );
    // const [data2] = await getJSON(
    //   `https://restcountries.eu/rest/v2/name/${c2}`
    // );
    // const [data3] = await getJSON(
    //   `https://restcountries.eu/rest/v2/name/${c3}`
    // );
    // console.log([data1.capital, data2.capital, data3.capital]);
    
    // note: use Promise.all([array of functions or API]) to run all the promises in parallel; it returns an array of promises; if there is a reject promise, it will crush and we need to do the erros handling
    const data = await Promise.all([ 
      getJSON(`https://restcountries.eu/rest/v2/name/${c1}`),
      getJSON(`https://restcountries.eu/rest/v2/name/${c2}`),
      getJSON(`https://restcountries.eu/rest/v2/name/${c3}`),
    ]);
    console.log(data.map(d => d[0].capital));
  } catch (err) {
    console.error(err);
  }
};
get3Countries('portugal', 'canada', 'tanzania');
```
**Other Promise method: race, allSettle and any**
````JavaScript
// Promise.race: it returns only the promise that is fulfilled first (completed first), not an array of promises like Promise.all()
(async function () {
  const res = await Promise.race([
    getJSON(`https://restcountries.eu/rest/v2/name/italy`),
    getJSON(`https://restcountries.eu/rest/v2/name/egypt`),
    getJSON(`https://restcountries.eu/rest/v2/name/mexico`),
  ]);
  console.log(res[0]);
})();


// Promise.race is very useful when it comes to stop a promise that might take too long to fulfill
const timeout = function (sec) {
  return new Promise(function (_, reject) {
    setTimeout(function () {
      reject(new Error('Request took too long!'));
    }, sec * 1000);
  });
};

// if the promise is taking more than 5 seconds to fulfill, reject it with an erro: Request took too long!
Promise.race([
  getJSON(`https://restcountries.eu/rest/v2/name/tanzania`),
  timeout(5),
])
  .then(res => console.log(res[0]))
  .catch(err => console.error(err));

// Promise.allSettled: returns an array of promises even one of the promise is rejected (it won't crush like Promise.all())
Promise.allSettled([
  Promise.resolve('Success'),
  Promise.reject('ERROR'),
  Promise.resolve('Another success'),
]).then(res => console.log(res));

// Promise.any [ES2021]: it similar to Promise.race(), but it ignores the rejected promise
Promise.any([
  Promise.resolve('Success'),
  Promise.reject('ERROR'),
  Promise.resolve('Another success'),
])
  .then(res => console.log(res))
  .catch(err => console.error(err));
````



