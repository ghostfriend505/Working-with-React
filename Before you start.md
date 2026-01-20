
<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">


# Before You Start React

  <p> React is easy to learn if you already know  some basics.</p>
  <p>Before jumping into React, make sure you understand the follwong concepts.</p>

<h4>This page will tell you everything you should know before starting React.</h4>


<h1> 1. HTML - The Structure of a Web Page </h1>

  <h3> What is HTML?</h3>

   HTML is used to create the structure of a web page
   Think of it as the skeleton of your website.

  React components return HTML-like code, so if you don't know HTML, React will feel confusing to you.

  <h4> Example </h4>
  
    <h1>Hello World</h1>
    <p>This is a paragraph</p>
    <button>Click me</button>

  This Creates:
  
  🔹 a heading
  
  🔹 a paragraph
  
  🔹 a button

  React will use the same tags, just inside javaScript.


<h4> What You Should Know </h4>
  
  You should understand:
    
  🔹 heading 
      
      <h1> This one create Heading </h1>
  
  🔹 text

      <p> This is a paragraph </p>
  
  🔹 container 

      <div> This is a container </div>
  
  🔹 input & buttons

        <button> I am a button </button>
  
  🔹 images & links

___________________________________________________________________________

<h1> 2. CSS - Making Things Look Good </h1>

  <h4>What is CSS </h4>

  CSS is used to style your websites (colors,spacing,layout).

  <h4>Example</h4>

      button {
      background: blue;
      color: white;
      padding: 10px;
      }

  This styles a button.

  In React, you'll use:

  🔹 CSS file
  
  🔹 inline styles
  
  🔹 CSS modules 
  
  🔹 libaries like Tailwing

  So you must understand basic CSS first.


  <h3> What You Should Know </h3>

  🔹 how to change colors 
  
  🔹 spacing (margin, padding)
  
  🔹 flexbox (VERY important)
  
  🔹 responsive layout

_____________________________________________________________________________

<h1>3. JavaScript - The Brain of React </h1>

<h3>What is JavaScript?</h3>

JavaScript is what makes your website interactive.

React is a JavaScript library, so if JS is weak, React will feel hard.

<h3>Variables</h3>

Used to store data:

    let name = "Ujjwal"
    const age = 22;

Their is one more type of Variable called (var) but we won't use that anymore because it causes a lot of issues


<h3>Functions </h3>

Functions do work for you:

    function greet() {
      return "Hello"
    }

React components are functions.

<h3>Arrays</h3>

Used to store multiple items:

    const users = [ "A", "B", "C"]

In React, you use array to show lists.


<h3> Objects</h3>

Used to store related data:

    const user = {
      name : "Ujjwal"
      age: 22
    }
    
React uses objects for props, state, data.


<h3> Array Methods (VERY IMPORTANT)</h3>

You will use these daily in React:

    users.map (user => user) 

This is how you render lists in React.

<h1>4. ES6 - Mordern JavaScript (Used Everywhere in React </h1>

React uses modern JavaScript features.


<h3>Arrow Functions</h3>

    const greet = () => "Hello"

<h3>Destructuring </h3>

    const {name} = user

<h3> Spread Operator</h3>

    const newUser = { ...user, city: "Delhi" }

React uses this for updating state.


<h1>5. DOM - What React Actually Controls </h1>

<h3> What is DOM?</h3>

DOM (document object model) is how the browser represents HTML in memory.

      document.querySelector("h1").innerText = "Hi";

React does this for you automatically, but you must understand:

🔹 what DOM is 

🔹 why React is faster

🔹 why we don't touch DOM directly in React


<h1>Tools You Need</h1>

<h3> Node.js </h3>

Required to run React apps.

<h3>npm</h3>

Used to install libaries.

<h3>VS Code</h3>

Best editor for React.

You can check YouTube how to install all of these in your computer 


<h1> If You Understand This, You're Ready </h1>

if you can:

  read HTML 

  style with CSS

  write JS functions

  understand arrays & objects

You are ready for React.

You don't need to be perfect - you'll learn while building.


<h1>Final Tip </h1>

|  React is not hard.

|  Weak JavaScript makes React feel hard.

Fix JS, and React becomes easy.



<h1> Exercise: Check Your Readiness for React </h1>

Try these small tasks.

If you can do most of them, you are readt to start React

If not, don't worry- this shows what you need to practice.

<h2>HTML Exercise</h2>

Write HTML that shows:

🔹 A heading with your name

🔹 A paragraph about you

🔹 a button saying "Start React"

<h2>CSS Exercise </h2>

<h4> Task 2: Style the button </h4>

Make the button: 

🔹blue background

🔹 white text

🔹 some padding

🔹 rounded corners

<h2>JavaScript Exercise</h2>

<h4> Task 3: Create variables</h4>

🔹 Create a variable age and name

<h4> Task 4: Create a function </h4>

🔹 Create a function greet ' Which returns Welcome to React '


<h4>Task 5: Array practice </h4>

🔹 Create a array called Topic and render it

<h4> Task:6 Object practice</h4>

🔹 Create a object with your name and level 


<h1> Answers </h1>


<h4> Task 1: </h4>

    <h1>Your Name</h1>
    <p>I am learning React</p>
    <button>Start React</button>
    
<h4> Task 2: </h4>

    button {
    background: blue;
    color: white;
    padding: 10px;
    border-radius: 6px;
    }

<h4> Task 3: </h4>

    const name = "My Name"
    const age  =  23

<h4> Task 4: </h4>

    function greet () {
      return "Welcome to React";
    }

<h4> Task 5:</h4>

      const topics = ["HTML", "CSS", "JavaScript"];

      topics.map (topic => console.log(topic));

<h4> Task 6: </h4>

      const student = {
       name: "Your Name",
       level: "Beginner"
      }




















































































































   
