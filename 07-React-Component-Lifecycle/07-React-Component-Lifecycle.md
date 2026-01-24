<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">


# React Component Lifecycle (Mounting, Updating, Unmounting)

## What is Component LifeCycle?

The lifecycle of a REact component is the journey of a component from creation to removal.

Every component goes through 3 main stages:

 - Mounting (Born)
 - Updating (Changes)
 - Unmounting (Removed)

React provides special methods (or hooks) to run code at each stage.


### 1. React Mounting  (Component Creation)

#### What is Mounting?

Mounting happnes when component is created and added to the DOM for the first time.

#### Why Mounting is important

- fetch data from API
- set initial values
- start timers
- add event listeners


#### Vite Example (Mounting)

``` bash

import {useEffect} from 'react'

function APP () {
  useEffect () => {
  console.log('Component Mounted')
  }

  return <h1> Mounted </h1>
}

export default App

```
[] means -> run once 


### 2. React Updating (Component Re-render)

#### What is Updating?

Updating happnes when:

- state changes
- props change
- parent re-renders

#### Example (Updating)

``` bash

import {useState, useEffect} from 'react'

function App() {
  const [count, setCount] = useState(0)

useEffect(() => {
  console.log ('Component Updated')
}, [count])

return (
  <button onClick= {() => setCount(count + 1)}>
    Count: {count}
  </button>
  )
}

```

Runs every time count changes.

### 3. React Unmounting (Component Removal)

#### What is Unmounting

Unmounting happnes when a component is removed from the screen.

Used for:

- CleanUp
- Remoce listeners
- Clear timers
- Stop SPI calls

#### Example (Unmounting)

``` bash
useEffect(() => {
  return () => {
    console.log('Component Unmounted')
  }
}, [])

```

## Lifecycle Stages (Simple Table)


    | Stage      | Hook                        |
    | ---------- | --------------------------- |
    | Mounting   | useEffect(() => {}, [])     |
    | Updating   | useEffect(() => {}, [deps]) |
    | Unmounting | return cleanup              |

## Lifecycle Methods (old vs New)

Old (Class Components)

- componentDidMount
- componentDidUpdate
- componentWillUnmount

New (Functional Components)

- useEffect

  useEffect replaces all lifecycle methods

### getDerivedStateFromProps 

used in class components to sync props to state

Not used in functional components directly

Insted, we use useEffect

### Interview Ready Points

- Lifecycle has 3 stages
- useEffect controls lifecycle
- Mount = empty dependency
- Update = dependency array
- Unmount = cleanup function

# Mini Project

``` bash
import {useEffect, useState} from 'react'

function App() {
  const [show, setShow] = useState(true)

  return (
    <div>
      <button onClick={()=> setShow(!show)}> Toggle </button>
      {show && <Child />}
    </div>
  )
}

function Child() {
  useEffect(() => {
    console.log('Mounted')

    return () => {
      console.log('Unmounted')
}
}, [])

return <h2> Child Component </h2>
}

```
### Questions

Q1.What is the Difference Between Rendering And Mounting?

### Answer 

A1. Renderinng vs Mounting (React)

    | Feature        | Rendering                         | Mounting                           |
    | -------------- | --------------------------------- | ---------------------------------- |
    | Meaning        | Preparing UI based on state/props | Adding component to DOM first time |
    | Happens when   | State or props change             | Component loads first time         |
    | How many times | Many times                        | Only once                          |
    | DOM update     | Virtual DOM (mostly)              | Real DOM                           |
    | useEffect      | No dependency needed              | `useEffect(() => {}, [])`          |
    | Triggered by   | State, props, parent render       | First render only                  |
    | Performance    | Very fast                         | One-time process                   |
    | Example        | `setCount()`                      | Component appears on screen        |


### Short Questions

Q1. In React, componentDidMount lifecycle method is called when____ 

Q2. How many stages are there in React js life cycle?  

Q3. Which hook is used for lifecycle?

Q4. When does mounting happen?

### Short Answers

A1. componentDidMount lifecycle method is called when the component is created for the first time.

A2. 3

A3. useEffet

A4. When a component is first rendered

A5. return function inside useEffect
