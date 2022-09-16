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
 // note: 'then' can accept two fall back function. The first fall back function will handle when the promise is successful fullfilled. The second fall back function will handle all the errors, for example, when we can't fetch the data from the api.
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





