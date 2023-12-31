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
* Effect of Attribute Setting: The effect of setting an attribute depends on the attribute itself. Some attributes control the element's behavior, appearance, or functionality. For example, setting the data-bs-dismiss attribute to "modal" on a Bootstrap button element might indicate that clicking the button should close a modal dialog.
* `add.click();` In JavaScript, most HTML elements have a click() method. This method, when called on a reference to an HTML element, simulates a user clicking that element. It triggers a click event on the element as if it had been clicked by the user.
* Use Cases:
_This approach is often used to automate interactions with web pages. For example, you might use it to programmatically click a button to submit a form or to trigger a modal dialog to open.
It's also used in automated testing and scripting to simulate user interactions with a web page._

* `add.setAttribute("data-bs-dismiss", "modal");`
In this case, you are setting the data-bs-dismiss attribute to the value "modal." This is often used in frameworks like Bootstrap to specify that a particular HTML element, when clicked, should dismiss or close a modal dialog associated with it. The "modal" value indicates the desired behavior.
* `add.setAttribute("data-bs-dismiss", "");`
* setting the data-bs-dismiss attribute to an empty string (""). This effectively removes the value associated with the attribute. In some cases, removing the attribute's value can disable or reset its behavior. It may no longer trigger the associated action.
In the first case, you're assigning a specific value ("modal") that typically indicates a particular behavior (e.g., closing a modal).
In the second case, you're removing the value by assigning an empty string, which might change or reset the behavior associated with the attribute, depending on how it's used in the underlying code or framework.
```

let data = [{}];

let acceptData = () => {
  data.push({
    text: textInput.value,
    date: dateInput.value,
    description: textarea.value,
  });

  localStorage.setItem("data", JSON.stringify(data));

  console.log(data);
  createTasks();
};

```
* `let data = [{}];` This line initializes an array called data with an empty object as its first element. This array will be used to store data objects representing tasks.
* `let acceptData = () => { ... };` This is the definition of a function named acceptData. This function will be called when a specific action occurs (likely when a user submits a form).
* `data.push({ ... });` Inside the acceptData function, a new object is created and pushed into the data array. This object represents a task and contains three properties: text, date, and description. These properties are filled with values extracted from the textInput, dateInput, and textarea elements.
* `localStorage.setItem("data", JSON.stringify(data));` After adding a new task to the data array, the entire data array is converted to a JSON string using JSON.stringify. Then, it's stored in the browser's localStorage under the key "data." This allows the data to persist between page reloads.
```
let createTasks = () => {
  tasks.innerHTML = ""; // Clear the contents of the 'tasks' element.

  // Use the 'map' method to iterate over the 'data' array and generate HTML for each task.
  data.map((x, y) => {
    return (tasks.innerHTML += `
      <div id=${y}>
        <span class="fw-bold">${x.text}</span>
        <span class="small text-secondary">${x.date}</span>
        <p>${x.description}</p>

        <span class="options">
          <i onClick= "editTask(this)" data-bs-toggle="modal" data-bs-target="#form" class="fas fa-edit"></i>
          <i onClick ="deleteTask(this);createTasks()" class="fas fa-trash-alt"></i>
        </span>
      </div>
    `);
  });

  resetForm(); // Call the 'resetForm' function, likely to clear the form inputs.
};
```
`tasks.innerHTML = "";` This line clears the contents of the HTML element with the id "tasks." It effectively removes any previously displayed tasks.
`data.map((x, y) => { ... });` The map method is used to iterate over the data array. For each task object in the array (x), it generates HTML code for that task. The y variable is likely the index of the task within the array.


#### Sample map() method
```
// The map method is used to iterate over the data array. 
const numbers = [65, 44, 12, 4];
const newArr = numbers.map(myFunction)

function myFunction(num) {
  return num * 10;
}
```
* `${y}:` The ${y} is using JavaScript template literals to interpolate the value of the y variable into the HTML. In the context of the code, y is likely an index that corresponds to the position of the task within the data array. So, for each task, the id attribute will be unique based on its position in the array.

* `x and y` are indeed parameters of the map method's callback function. This code is using the map method to iterate over the data array, and for each element in the array, the callback function is called with two parameters:

* `x:` This parameter represents the current element in the array, which in this context is each task object. So, x is a reference to the current task being processed.

* `y:` This parameter represents the index of the current element in the array. It indicates the position of the task within the array. y is an integer that represents the index of the current task.

```
data.map((x, y) => {
  // ... HTML template for each task
});
```
```
map(callbackFn)
map(callbackFn, thisArg)
```
* The map() method is an iterative method. It calls a provided callbackFn function once for each element in an array and constructs a new array from the results.
```
          <span class="options">
            <i onClick= "editTask(this)" data-bs-toggle="modal" data-bs-target="#form" class="fas fa-edit"></i>
            <i onClick ="deleteTask(this);createTasks()" class="fas fa-trash-alt"></i>
          </span>
```
* `<span class="options">`: This span element is used to group the task options, which typically include an "Edit" option and a "Delete" option.
* <i onClick="editTask(this)" data-bs-toggle="modal" data-bs-target="#form" class="fas fa-edit"></i>: This i element represents the "Edit" option. Let's break down its attributes and behavior:
`onClick="editTask(this)":` This onClick attribute specifies that when the "Edit" icon is clicked, it should call the editTask function and pass the this reference as an argument. The this reference typically represents the clicked icon, allowing you to identify which task is being edited.
`data-bs-toggle="modal" data-bs-target="#form":` These are Bootstrap attributes used to open a modal with the id "form" when the "Edit" icon is clicked. This is typically used for editing the task.
* <i onClick="deleteTask(this);createTasks()" class="fas fa-trash-alt"></i>: This i element represents the "Delete" option. Here's what it does:
`onClick="deleteTask(this);createTasks()":` This onClick attribute specifies that when the "Delete" icon is clicked, it should first call the deleteTask function, passing the this reference as an argument (likely to identify which task is being deleted). After that, it calls the createTasks function. This sequence of actions typically deletes the task and then refreshes the list of tasks
```
let deleteTask = (e) => {
 
  e.parentElement.parentElement.remove();
  data.splice(e.parentElement.parentElement.id, 1);
  localStorage.setItem("data", JSON.stringify(data));
  console.log(data);
  
};

```
#### Parent element DOM study

* In the deleteTask function, the line `e.parentElement.parentElement.remove()` is used to remove the grandparent element of the HTML element referenced by e from the DOM.

* `e:` This represents an HTML element (likely an icon or button) that triggered the delete action. This element is assumed to have a parent element.The `this` keyword, when used in the onClick event handler, refers to the element that triggered the event. In this case, it's the delete icon <i> element. So, in the deleteTask function, e represents this delete icon element.

* `.parentElement:` This property accesses the direct parent element of the element referenced by e. It represents the first level of the parent-child relationship.

* `.parentElement:` This is used again to access the parent element of the parent element, which effectively represents the grandparent element of the element referenced by e.

* `.remove():` This method is called on the grandparent element to remove it and all its descendants from the DOM.
```
The DOM tree mentioned here is not from the default HTML. Instead, we created a function called createTask and added some updates. These updates comprise a list of tasks displayed on the webpage, and we manipulate this HTML content within the deleteTask and editTask functions using the onclick attribute to call the functions and pass the argument 'e' to the function.

We manipulate this DOM tree using the parentElement property in JavaScript(not the defalut HTML file).
```

* `data.splice(taskId, 1):` This line uses the splice method to remove one element from the data array at the index specified by taskId. This corresponds to the specific task being deleted.
`syntax` = array.splice(index, howmany, item1, ....., itemX)
`index` =	Required.
The position to add/remove items.
Negative value defines the position from the end of the array.
`howmany` =	Optional.
Number of items to be removed.
`item1, ..., itemX` =	Optional.
New elements(s) to be added.
* By examining the arguments you pass to splice, you can determine whether it is used to remove, add, or both remove and add elements in your code.

```
//To remove one element at index 2:
array.splice(2, 1);

//To add one element at index 2 without removing any elements:
array.splice(2, 0, 'newElement');

//To remove two elements starting from index 3 and add two new elements:
array.splice(3, 2, 'newElement1', 'newElement2');

If howmany is greater than 0, it will remove that number of elements starting from the index. 
if how many is not present nothing will be removed.
```

* `localStorage.setItem("data", JSON.stringify(data))`: This line updates the data in the browser's localStorage to reflect the changes made by removing a task from the array. This effectively updates the stored data with the latest version of the data array.

```
let editTask = (e) => {
  let selectedTask = e.parentElement.parentElement;

  textInput.value = selectedTask.children[0].innerHTML;
  dateInput.value = selectedTask.children[1].innerHTML;
  textarea.value = selectedTask.children[2].innerHTML;

  deleteTask(e);
};
```
* `let selectedTask = e.parentElement.parentElement;`: This line selects the parent element of the element referenced by e, which appears to be the grandparent element. This element represents the task you want to edit.
* The `innerHTML` property sets or returns the HTML content (inner HTML) of an element.
* Yes, you're correct. If x.text, x.date, and x.description are all changed to empty values, and those values are used to update the textInput, dateInput, and textarea elements, it would result in empty input fields. If the task data is empty, it could lead to an empty <div> element in the tasks container.
* If all the task data becomes empty, it would lead to an empty task entry within the tasks container, and the <span> with the class "options" would also be empty or not displayed because there would be no content to display within that task entry.
```
let resetForm = () => {
  textInput.value = "";
  dateInput.value = "";
  textarea.value = "";
};
```
* The `resetForm` function is a JavaScript function that resets the values of specific input elements to empty or blank values. It's designed to clear the values of textInput, dateInput, and textarea elements.

```
(() => {
  data = JSON.parse(localStorage.getItem("data")) || [];
  console.log(data);
  createTasks();
})();

```
* It will be `automatically` invoked as soon as it's encountered in the script. It doesn't depend on any other functions or events to trigger its execution. This `IIFE` is executed immediately when the script is loaded, and it serves the purpose of initializing the application by retrieving data from local storage, logging the data, and calling the createTasks function to populate the UI with task data from local storage.
* data = JSON.parse(localStorage.getItem("data")) || []: Inside the function, it retrieves data from the browser's localStorage. The localStorage.getItem("data") call retrieves a stored item named "data." If there's data stored, it's parsed from a JSON string into a JavaScript object using JSON.parse(). If there's no data in the storage or it's not valid JSON, an empty array [] is used as a default value. The retrieved or default data is assigned to the data variable.
```
Logical OR (||) Operator: The || operator is used to provide a default value in case the left side of the expression is falsy. If the value retrieved from local storage is falsy (e.g., null or undefined), then an empty array ([]) is used as the default value for data.
```
* createTasks(): Finally, it calls the createTasks function, presumably to populate the UI with tasks based on the retrieved or default data.
