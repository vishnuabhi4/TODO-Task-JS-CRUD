# TODO-Task-JS-CRUD
### Javascript Logic Flow
```
let form = document.getElementById("form");
```
* document: In JavaScript, the document object represents the web page or document in the browser. It provides access to the HTML content of the page.
* document.getElementById("form"): This part of the code is calling the getElementById method of the document object. The method takes a single argument, which is the id attribute value of the HTML element you want to retrieve.
* let form = ...: The result of document.getElementById("form") is assigned to a variable named form using the let keyword. This creates a new variable in the current scope.
```
form.addEventListener("submit", (e) => {
    e.preventDefault();    // Prevent the default form submission behavior
    formValidation();       // Call the formValidation function
});
```
