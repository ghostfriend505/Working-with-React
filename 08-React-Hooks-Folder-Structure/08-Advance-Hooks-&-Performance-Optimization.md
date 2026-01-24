<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">


# Advanced Hooks & Performance Optimization

## 1. Why Advanced Hooks Exist 

As apps grow:

- state becomes complex
- re-renders become slow
- logic gets repeated
- components get messy

Advanced hooks solve thes problems by:

- optimizing proformance
- organizing logic
- avoiding unnecessary renders
- sharing Logic cleanly

## 2. useRef - Access DOM & Persist Values

What is useRef?

useRef let's you strore a value without re-rendering the component.

Used for:

- focusing input
- storing previous values
- timers
- accessing DOM

``` bash
import{useRef} from 'react'

function App() {
  const inputRef = useRef(null)

  return (
    <>
      <input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>
          Focus Inpur
      </button>
    </>  
  )
}

export default App
```
##  3. useMemo - Optimize Heavy Calculations

What is useMemo?

It remembers a calculated value so React doesn't recalculate it on every render.

#### Example

``` bash

import { useMemo, useState} from 'react'

function App() {
  const [count, setCount] = useState(0)
  const [dark, setDark] = useState(false)

  const slowValue - useMemo (() => {
    console.log ('Calculation...')
    let total = 0
    for (let i =0; i < 1e7; i++) total += 1
    return total
}, [])

  return (
    <div style={{ background: dark ? '#000' : '#fff' }}>
      <button onClick={() => setCount(c => c + 1)}>+</button>
      <button onClick={() => setDark(d => !d)}>Toggle Theme</button>
      <p>{slowValue}</p>
    </div>
  )
}

```

## 4. useCallback - Optimize Functions

What is useCallback?

It remembers a function so it doesn't get recreated on every render.

Used when passing functions to child components.

#### Example

``` bash

import { useCallback, useState } from 'react'

function App() {
  const [count, setCount] = useState(0)

  const handleClick = useCallback(() => {
    setCount(c => c + 1)
  }, [])

  return <Child onClick={handleClick} />
}

function Child({ onClick }) {
  console.log('Child rendered')
  return <button onClick={onClick}>Click</button>
}


```

## 5. useReducer - Manage Complex State

What is useReducer?

Use when:

- many state values
- many actions
- complex logic

``` bash

import { useReducer } from 'react'

function reducer(state, action) {
  switch (action.type) {
    case 'inc':
      return { count: state.count + 1 }
    case 'dec':
      return { count: state.count - 1 }
    default:
      return state
  }
}

function App() {
  const [state, dispatch] = useReducer(reducer, { count: 0 })

  return (
    <>
      <button onClick={() => dispatch({ type: 'inc' })}>+</button>
      <button onClick={() => dispatch({ type: 'dec' })}>-</button>
      <p>{state.count}</p>
    </>
  )
}


```

## 6. Custom Hooks - Reuse Logic 

What is Custom Hook?

A function that:

- starts with use
- contains hooks
- returns reusable logic

``` bash

import { useState } from 'react'

export function useToggle () {
    const [on. setOn] = useState(false)
    return [on, () =< setOn (o => !o)]
  }

```

Use: 

``` bash
const [open, toggle] = useToggle()
```

## 7. Performance Optimization Summary 

    | Problem             | Solution    |
    | ------------------- | ----------- |
    | Slow calculation    | useMemo     |
    | Function re-created | useCallback |
    | Complex state       | useReducer  |
    | DOM access          | useRef      |
    | Logic reuse         | Custom hook |

## 8. Common Mistakes 

❌ Using useMemo everywhere

❌ Using useCallback without need

❌ Over-optimizing too early

❌ Not using dependency array correctly

## Part 1: Code-Based Question 

Question

Create a React app that:

- Uses useReducer for counter
- Uses useRef to focus input
- User useMemo for heavy calculation
- Uses useCallback for button click
- Uses functional components only

## Part 2: Long Answer Questions

Q1. Explain why useReducer is better than useState in complex applications.

Q2. Explain how useMemo improves performance.

Q3. Explain the purpose of custom hooks and their benefits


## Part 3: Short Answer Questions (Quick Revision)

Q1. What hook is used to manage complex state?

Q2. Which hook accesses DOM elements?

Q3. Which hook memorizes a value?

Q4. Which hook memorizes a function?

Q5. Which hook replaces class lifecycle methods?

Q6. What must custom hooks start with?

Q7. Does useRef cause re-render?

Q8. When should you use useMemo?

Q9. Which hook is used for performance optimization?

Q10. Which hook is best for logic reuse?


## Part 1: Answer

``` bash

import { useReducer, useRef, useMemo, useCallback } from 'react'

function reducer(state, action) {
  switch (action.type) {
    case 'inc':
      return { count: state.count + 1 }
    case 'dec':
      return { count: state.count - 1 }
    default:
      return state
  }
}

function App() {
  const [state, dispatch] = useReducer(reducer, { count: 0 })
  const inputRef = useRef(null)

  const heavy = useMemo(() => {
    let sum = 0
    for (let i = 0; i < 1e7; i++) sum += i
    return sum
  }, [])

  const handleClick = useCallback(() => {
    dispatch({ type: 'inc' })
  }, [])

  return (
    <div>
      <input ref={inputRef} placeholder="Focus me" />
      <button onClick={() => inputRef.current.focus()}>Focus</button>

      <h2>Count: {state.count}</h2>
      <button onClick={handleClick}>+</button>

      <p>Heavy calc: {heavy}</p>
    </div>
  )
}

export default App

```

## Part 2: Answers

A1.useReducer is better when state logic becomes complex, 
such as when multiple actions can update the same state. 
It centralizes logic in one reducer function, making code predictable, 
easier to debug, and easier to test. It also avoids multiple useState calls 
and keeps updates organized.

A2.useMemo prevents expensive calculations from running on every render.
It stores the calculated value in memory and recalculates only when dependencies change. 
This improves performance especially when working with large loops, filtering, 
or expensive computations.

A3. Custom hooks allow developers to reuse logic across multiple components. 
Instead of copying code, logic is placed in a hook function and reused cleanly. 
This improves maintainability, reduces duplication, and makes components simpler.

## Part 3: Short Answers

A1. useReducer

A2. useRef

A3. useMemo

A4. useCallback

A5. useEffect

A6. use

A7. No

A8. For expensive calcilations

A9. useMemo/ useCallback

A10. Custom hook
