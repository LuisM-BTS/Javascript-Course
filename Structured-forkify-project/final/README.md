# forkify Project

Recipe application with custom recipe uploads.

Sure, here's the README.md in English:

---

# Forkify Recipes

This project is a web application for searching and storing cooking recipes. It utilizes the Forkify API to fetch recipe data and provides features such as search, detailed recipe view, bookmarks management, and the ability to add new recipes.

## Setup

The `config.js` file contains the application configuration, including details such as the API URL, request timeout, number of results per page, and more.

```javascript
export const API_URL = 'https://forkify-api.herokuapp.com/api/v2/recipes/';
export const TIMEOUT_SEC = 10;
export const RES_PER_PAGE = 10;
export const KEY = '<YOUR_KEY>';
export const MODAL_CLOSE_SEC = 2.5;
```

## Controller

The `controller.js` file defines control functions to handle the application logic, such as loading recipes, searching results, pagination, bookmarks management, adding recipes, etc.

```javascript
// Control functions for loading recipes, searching results, etc.
```

## Helpers

The `helpers.js` file provides helper functions to handle asynchronous requests and error handling, such as timeout and response handling.

```javascript
// Helper functions for handling asynchronous requests and errors
```

## Model

The `model.js` file contains the data model of the application, including the recipe state, search results, and bookmarks, as well as functions to load recipes, search results, update servings, add or remove bookmarks, and more.

```javascript
// Data model and functions for loading recipes, searching results, etc.
```

## Views

The project includes various views in the `views` folder, such as the recipe view, search view, results view, pagination view, bookmarks view, and view for adding new recipes.

```javascript
// Views for displaying recipes, search results, etc.
```

## Initialization

The `init.js` file initializes the application by binding control functions to user events and setting up the initial application state.

```javascript
// Initialization of the application and binding of control functions to user events
```

## Running the Project

To run the project, simply run the commands 'npm install' and ' 'npm start' and it will open the `index.html` file in your web browser and start exploring and enjoying the available recipes.

---

Feel free to customize this README according to the specific needs of your project, including more details about installation, usage, and any other relevant information for users and contributors.
