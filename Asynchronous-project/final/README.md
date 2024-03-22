
# JavaScript Project

This project is a web application that utilizes JavaScript to interact with external APIs and perform various asynchronous operations, such as fetching country data, images, and geolocation. The code addresses advanced JavaScript concepts including promises, async/await, DOM manipulation, and error handling.

## Key Features

- **AJAX with XMLHttpRequest**: Makes asynchronous calls to the REST Countries API to fetch detailed information about countries and their neighbors.
- **Promises and Chaining**: Uses promises to handle asynchronous operations and chains them to execute code sequentially.
- **Async/Await**: Employs async/await syntax to write asynchronous code in a more readable and structured manner.
- **DOM Manipulation**: Dynamically renders country data and image elements in the DOM using JavaScript.
- **Geolocation API**: Utilizes the browser's Geolocation API to determine the user's location based on their device's GPS coordinates.
- **Error Handling**: Implements error handling using try...catch blocks and catch() methods on promises to capture and handle errors occurring during asynchronous operations.
- **Parallel Promise Execution**: Executes multiple promises in parallel using Promise.all to wait for all promises to resolve before proceeding.

## Usage

To test the application, simply download the files and open them in a JavaScript-compatible web browser. Ensure you have an active internet connection so the application can make calls to external APIs.

## Code Examples

Below are examples of how some of the main features of the code are used:

```javascript
// Make AJAX call to REST Countries API using XMLHttpRequest
const request = new XMLHttpRequest();
request.open('GET', `https://restcountries.eu/rest/v2/name/${country}`);
request.send();

// Chain promises to handle asynchronous operations sequentially
getJSON(`https://restcountries.eu/rest/v2/name/${country}`)
  .then(data => renderCountry(data[0]))
  .catch(err => console.error(`${err.message} 💥`));

// Use async/await to write asynchronous code in a more readable way
const whereAmI = async function () {
  try {
    const pos = await getPosition();
    const { latitude: lat, longitude: lng } = pos.coords;
    const resGeo = await fetch(`https://geocode.xyz/${lat},${lng}?geoit=json`);
    const dataGeo = await resGeo.json();
    console.log(`You are in ${dataGeo.city}, ${dataGeo.country}`);
  } catch (err) {
    console.error(`${err} 💥`);
    renderError(`💥 ${err.message}`);
  }
};
```

## Contribution

If you'd like to contribute to this project, feel free to submit a pull request!

## License

This project is licensed under the [MIT License](LICENSE).

