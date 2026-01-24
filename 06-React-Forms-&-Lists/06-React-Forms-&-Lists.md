<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">


# Part 1: React Forms 

## 1. What is Form in React?

A form is used to collect user input and send it to the application.

Example:

- Login form
- signup form
- search box
- contact form
- feedbacl form

In React, forms are handled using state and events.

## 2. Why React Forms are Different

In normal HTML:

- browser controls input

In React:

- React controls input (controlled components)

This makes data:

- predictable
- easy to validate
- easy to manage
- easy to send to server

## 3. Controlled Form Example 

App.jsx 

    import { useState } from 'react'

    function App () {
      const [name, setName] = useState('')
      const [email, setEmail] = useState('')

      const handleSubmit = (e) => {
        e.preventDefault()
        alert(`Name: ${name}, Email: ${email}`)
      }

      return (
        <form onSubmit={handleSubmit}>
        <input
          placeholder="Name"
          value={name}
          onChange={(e) => setName(e.target.value)}
        />

        <input 
          placeholder="Eail"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />

        <button type="submit"> Submit </button>
      </form>
      )
    }

    export default App


## 4. Why Controlled Forms are Useful

- React always knows form data
- Easy validation
- Easy reset
- Easy submit
- Easy debugging
- No DOM access needed
- Works with state
- Predictable behavior
- Secure handling
- Industry standard


## 5. Multiple Inputs Using One State

    const [form, setForm] = useState ({ name: '', email: ''})

    const handleChange = (e) => {
      setForm({
        ...form,
        [e.target.name]: e.target.value
      })
    }


    <input name="name" onChange={handleChange} />
    <input name="email" onChange={handleChange} />

# Part 2: React Lists

## 6. What is List in React?

A list is used to display multiple items using an array.

Example:

- users
- products
- todos
- messages
- posts

React uses .map() to render lists.

## 7. Why Lists are important

List help:

- show dynamic data
- render API responses
- build dashboards
- buil tables
- show repeated UI

## 8. Basic List Example

    const fruits = ['Apple','Banana','Mango']

    <ul> {fruits.map(fruit => (
      <li key={fruit}> {fruit} </li>
    ))}
    </ul>

## 9. The (key) in Lists

Keys help React:

- identify items
- update efficiently
- avoid bugs

      <li key={item.id}> {item.name} </li>


## 10. Multiple Input Feilds

- We can control the values of more than one input field by addng a name attribute to each element.
- We will initialize our state with an empty object
- To access the in the evenet handler use the

        event.target.name & event.target.value    STNTAXX.

- To update the state, use square brackets [] around the property name.
   

#### Example

- Write a form with TWO INPUT FIELDS:

  App.jsx

      import {useState} from 'react'

        function App() {
          const [input, setInputs] = useState({})
          const handleChange = (event) => {
            const name = event.target.name;
            const value = event.target.value;
          setInputs(values => ({...values, [name]: value}))
          }
          const handleSubmit = (event) => {
            event.preventDefault();
            alert(inputs);
          }
          return (
            <form onSubmit={handleSubmit}>
            <label>Enter your name:
            <input
              type="text"
              name="username"
              value={inputs.username || ""}
            onChange={handleChange}
            />
            </label>
          <label>Enter your age:
            <input
              type="number"
              name="age"
              value={inputs.age || ""}
              onChange={handleChange}
              />
            </label>
              <input type="submit" />
              </form>
            )
          }


# Part 3: Form + List Combined Example

#### Example: making TODO APP 

Requirements:

- form to add todo
- list to show todos
- key usage
- state usage
- events usage
- controlled input

#### Full Code: App.jsx

    import {useState} from 'react'

      function App () {
        const [todo, setTodo] = useState('')
        const [todos, setTodos] = useState([])

        const addTodo = (e) => {
        e.preventDefault()

        setTodos([
          ...todos,
          {id: Date.now(), text: todo}
        ])
        setTodo('')
        }

        return (
          <div> 
            <h2> Todo App </h2>

            <form onSubmit={addTodo}>
              <input
                value={todo}
                onChange={(e) => setTodo(e.target.value)}
                placeholder="Enter todo"
                />
                <button> Add </button>
            </form>
            <ul> 
              {todo.map(t => (
              <li key={t.id}> {t.text} </li>
              ))}
            </ul>  
          </div>
        )
      }
    export default App

## What this example uses

| Concept          | Used |
| ---------------- | ---- |
| Form             | ✅    |
| Controlled input | ✅    |
| State            | ✅    |
| Events           | ✅    |
| List             | ✅    |
| key              | ✅    |
| Vite             | ✅    |



## Exercise 

Q1. Why do we use controlled forms?

Q2. How do we render a list in React?

Q3. Why is key required?

Q4. Create a simple list

## Short Answer type

Q1. In which part does the form validation occurs in React? 

Q2. What is the purpose of data format validation in React? 

Q3. How can you set a default value for an uncontrolled form field in ReactJs? 


## Answers 

A1. Because React needs to control input values to make data predictable and manageable.

A2. By using .map() and returning JSX elements with unique keys.

A3. To help React identify list items and update them efficiently.

A4. 
      
    {items.map(i => <li key={i.id}>{i.name}</li>)}

## Short Answers 

A1. Server

A2. Data correctness

A3. By using the defaultValue property

## Summary 

- Forms collect user input
- Controlled forms use state
- Lists display dynamic data
- Keys help React update UI
- Forms + List build real apps
