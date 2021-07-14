# Asynchronism

- Reference: [The Complete JavaScript Course 2018](https://www.udemy.com/the-complete-javascript-course/)

- [Asynchronism](#asynchronism)
  - [Promise hell](#promise-hell)
  - [Async/Await method](#asyncawait-method)
  - [To fetch data using Vanilla.js](#to-fetch-data-using-vanillajs)

## Promise hell

```js
const getIds = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve([523, 883, 432, 974]);
  }, 1500);
});

const getRecipe = recId => {
  return new Promise((resolve, reject) => {
    setTimeout(id => {
      const recipe = {
        title: 'Fresh tomato pasta',
        publisher: 'Jonas',
      }
      resolve(`${id}: ${recipe.title}`);
    }, 1500, recId);
  });
};

const getRelated = publisher => {
  return new Promise((resolve, reject) => {
    setTimeout(pub => {
      const recipe = {
        title: 'Italian Pizza',
        publisher: 'Jonas',
      }
      resolve(`${pub}: ${recipe.title}`);
    }, 1500, publisher);
  });
};

getIds
  .then(Ids => {
    console.log(Ids); // [523, 883, 432, 974]
    return getRecipe(Ids[2]);
  })
  .then(recipe => {
    console.log(recipe); // 432: Fresh tomato pasta
    return getRelated(recipe.publisher);
  })
  .then(recipe => {
    console.log(recipe);
    // if you use "return getRelated(recipe.publisher)",
    // the result is "undefined: Italian Pizza"
    return getRelated('Jonas Schemdtamnn');
  })
  .then(recipe => {
    console.log(recipe);
    // if you use "return getRelated('Jonas Schemdtamnn');",
    // the result is "Jonas Schemdtamnn: Italian Pizza"
  })
  .catch(error => {
    console.log('Error!');
  });
```

> [Back to top](#basic-javaScript-mechanism)

## Async/Await method

```js
async function getRecipesAW() {
  const Ids = await getIds;
  console.log(Ids); // [523, 883, 432, 974]
  const recipe = await getRecipe(Ids[2]);
  console.log(recipe); // 432: Fresh tomato pasta
  const related = await getRelated('Jonas Schemdtamnn');
  console.log(related); // Jonas Schemdtamnn: Italian Pizza

  return recipe;
}

const rec = getRecipesAW();
console.log(rec); // Promise object

getRecipesAW().then(result => console.log(`${result} is the best ever!`));
// 432: Fresh tomato pasta is the best ever!
```

> [Back to top](#basic-javaScript-mechanism)

## To fetch data using Vanilla.js

- AJAX: Asynchronous JavaScript And Xml

- API: Application Programming Interfac

- Weather api: [https://www.metaweather.com/api](https://www.metaweather.com/api)

- A website used to avoid CORE: [https://crossorigin.me](https://crossorigin.me)

```js
function getWeather(woeid) {
  fetch(`https://crossorigin.me/https://www.metaweather.com/api/location/${woeid}`)
    .then(result => {
      console.log(result); // [Object]; TL
      return result.json();
    })
    .then(data => {
      console.log(data); // [Object]; TL but it is data we want
      const today = data.consolidated_weather[0];
      console.log((`Temperatures in ${data.title} stay between ${today.min_temp} and ${today.max_temp}.`));
    })
    .catch(error => console.log(error));
}
getWeather(2487956); // blablabla
getWeather(44418); // blablabla

// To rewrite codes using Async/Await
async function getWeather(woeid) {
  try {
  const result = await fetch(`https://crossorigin.me/https://www.metaweather.com/api/location/${woeid}`);
  const data = await result.json();
  const today = data.consolidated_weather[0];
  console.log(data); // [Object]; TL but it is data we want
  console.log((`Temperatures in ${data.title} stay between ${today.min_temp} and ${today.max_temp}.`));
  } catch(error) {
    console.log(error);
  }
}
getWeather(2487956); // blablabla
let dataLondon;
getWeather(44418).then(data => {
  dataLondon = data;
  console.log(dataLondon);// [Object]; TL but it is data we want
});
console.log(dataLondon); // undefined
dataLondon = getWeather(44418); // blablabla
console.log(dataLondon); // Promise object
```

> [Back to top](#basic-javaScript-mechanism)
