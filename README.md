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
* `form.addEventListener("submit", (e) => { ... });` This code attaches an event listener to an HTML form element represented by the form variable. It listens for the "submit" event, which occurs when the form is submitted (e.g., when the user clicks a submit button or presses Enter inside a form field).
* `(e) => { ... };` This part defines an arrow function that serves as the event handler. The e parameter represents the event object, which contains information about the event that triggered the listener.
* `e.preventDefault();` Inside the event handler, e.preventDefault() is called. This line prevents the default behavior of form submission. By default, when a form is submitted, the browser reloads the page or navigates to a new page. Calling e.preventDefault() prevents that default behavior, allowing you to handle the form submission with custom logic.

***In web development, when a form is submitted without any JavaScript intervention, the browser typically performs a "default" action, which is to send the form data to the server and either refresh the current page or navigate to a new page based on the form's action attribute.***

***However, there are scenarios where you might want to customize the behavior when a form is submitted. You may want to perform client-side validation, send data to the server asynchronously (e.g., using AJAX), or manipulate the DOM based on the form data without navigating to a new page.***

***This is where e.preventDefault() comes into play. When you call e.preventDefault() within an event handler (such as a form submit event handler), it tells the browser, "Don't perform the default action associated with this event." In the case of a form submission, it prevents the page from being reloaded or navigating to a new page.***

***After preventing the default action, you have the freedom to write your own custom logic for handling the form submission. This might involve validating the form data, making an AJAX request, updating the DOM, displaying messages to the user, or anything else you need to do.***
* `formValidation();` After preventing the default behavior, the formValidation() function is called. This function is presumably defined elsewhere in your code, and its purpose is to perform validation or other actions related to the form's data.
```
let add = document.getElementById("add");
add.setAttribute("data-bs-dismiss", "modal");
add.click();
```
* Assigning to a Variable: When you store this reference in a variable like add, you're essentially creating a link or a reference to the HTML element.
* `add.setAttribute("data-bs-dismiss", "modal");` This line sets an attribute on the HTML button element (referenced by add). The attribute being set is data-bs-dismiss, and it's assigned the value "modal." This attribute is often used in Bootstrap to define the behavior of elements that can dismiss or close Bootstrap modals. When you add this attribute to the button element, it typically indicates that clicking the button will close a modal associated with it.
* ***Attribute:HTML elements can have various attributes, depending on their type and purpose. For example, a button element might have attributes like id, class, type, name, and custom attributes like data-bs-dismiss***