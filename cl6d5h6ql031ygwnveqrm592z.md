## Why is it time to move on to ReactJS?

Vanilla js is known as plain old Javascript and it’s basically the javascript written without using any libraries.
React is a JS library used for building UI. It allows us to make complex UIs using components.

## What you actually get in ReactJS CODE Isolation in React ?

In Vanilla JS, if we want to update some piece of HTML. That piece of code may reside in multiple JS files. So, it becomes hard for the developer to track all these files and they have to keep all the files open at once. 
In React, we split our code into components and each component maintains all the code needed for both display and updates to UI. Therefore, updated code is next to display code, which makes complex apps much easier to understand. 


![components in reactjs](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yi918d2dh2p9bzvmtji6.png)


## We get better Data Handling in React

In Vanilla JS, our data is stored in a model called DOM(Document Object Model) which is created and maintained by the browser. 
If a user gives input in a form, the developer needs to extract that data by finding it in the DOM first and then extracting its value. Which becomes a very tedious job.
But, In React we have a concept called “controlled-components” which sets the text value in a JS Object as the user types it. In general, React stores data in regular JS variables.
Ex : 
```js
const [input, setInput] = useState(“”)
```


## Hooks in React 
In React we have a concept called Hooks which provides benefits like Reusability, Readability, and Testability. You get some built-in hooks like useState, useEffect, useReducer, useRef etc, which helps in rapid development.
Improves Readability  For example “useContext” hook has been a blessing for improving the readability of JSX as it allows context values to be read outside of JSX.
Aside from code it’s easier to read the component tree in react dev tools when debugging.
 




## Using React in Web Apps 
Using React JS in creating web applications is a cherry on cake. Data gets dynamically updated in web pages without requiring them to be reloaded at each time. When the user clicks on a button in the page data can be presented to the user without reloading the page every time. This gives the user a good interaction with the web site. 






## Conclusion 
Vanilla JS is awesome but it’s not a great alternative when it comes to building huge applications with complex functionalities. Also, you can’t create complex UIs(it will take too much of time). On the other hand, React allows us to create reusable components. So, React is Better to learn & use in every aspect of rapid Development. 

 
