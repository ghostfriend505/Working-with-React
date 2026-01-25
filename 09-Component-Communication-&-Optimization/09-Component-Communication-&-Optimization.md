<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Component Communication & Optimization 

## 1. React Memo (Performance Optimization)

#### What is React.memo?

React.memo is a higher-order component that prevents unnecessary re-renders of a component.

React normally re-renders child components when parent re-renders --- even if props didn't change.
React.memo stops this.

Example 

``` bash
function Child({ vlaue }) {
  console.log('Child renderd')
  return <p> {value} </p>
}
```

Child re-renders every time parent renders ❌

Example (With Memo)

``` bash
import {memo} from 'react'

const Child = memo (({value}) => {
  console.log('Child rendered')
  return <p> {value} </p>
})

export default Child
```

Now child re-renders only when props change ✅

## 2. Stateless Components Commnication

Stateless components:

- do not have state
- depends on props
- are pure UI components

They receive data from parent and diplay it.

Example

``` bash
function Display({ text }) {
  return <h2> {text} </h2>
}
```

## 3. Child to Parent Communication

React is one-way data flow (parent -> child), but child can talk to parent using callback function.

Example 

``` bash
function Parent () {
  const getDta = (data) => {
  console.log(data)
}

return <Child onSecnd={getData} />
}

function Child () {
  return <button onClick={() => onSend('Hello Parent')} />
}
```

## 4. Communication Between Non-Related Components

When components are not related:

- use lifted state
- use Context API
- use global store

Example (Context)

``` bash
const DataContext = createContext()

function App() {
  return (
    <DataContext.Provider value="Hello">
      <ComponentA />
    </DataContext.Provider>
  )
}

function Components() {
  const data = useContext(DataContext)
  return <p> {data} </p>
}

```

## 5. Props Value vs Children Props

Props Value 

``` bash
<Button text="Login" />
```

Children Props

``` bash
<Button> Login </Button>
```

``` bash
function Button({ children }) {
  return <button> {children} </button>
}
```

## 6. Summary Table 

    | Concept    | Use                       |
    | ---------- | ------------------------- |
    | React.memo | Prevent re-render         |
    | Props      | Parent to child           |
    | Callback   | Child to parent           |
    | Context    | Non-related communication |
    | Children   | Flexible UI               |


## Exercises

### Part 1. Code-Based Question

Create a app that:

- Uses React.memo
- Has parent & child communication
- Uses children props
- Avoids unnecessary re-renders

### Part 2. Long Answer Questions

Q1. Q1. Why is React.memo used?

Q2. Explain child-to-parent communication in React.

Q3. How do non-related components communicate?

### Part 3. Short Answer Questions

Q1. What does React.memo do?

Q2. What is stateless component?

Q3. How does child talk to parent?

Q4. How do siblings communicate?

Q5. What is children prop?

Q6. What hook uses context?

Q7. What causes re-render?

Q8. What is optimization?

Q9. What is memoization?

Q10. When to use memo?

## Answer 

### Part 1.

``` bash
import {useState, memo} from 'react'

const Child = memo (({ onClick, children}) => {
  console.log('Child rendered')
  return <button onClick={onClick} > {children} </button>
})

function App() {
  const [count, setCount] = useState(0)

  return (
    <div>
      <h2> Count: {count} </h2>
      <Child onClick=() => setCount(count + 1 )}>
        Increment
      </Child>
    </div>
  )
}

export default App
```

## Part 2. 

A1. It prevents unnecessary re-renders by memoizing the component output when props do not change,
    improving performance.

A2. Child components communicate with parents using callback functions passed as props, 
    allowing data flow upward.

A3. Using Context API or lifting state to a common parent.

## Part 3. 

A1. Prevents unnecessary re-render

A2.  Component with no state

A3. Callback props

A4.  Lift state up

A5. Nested JSX content

A6. useContext

A7. State/props change

A8. Improving performance

A9. Caching result

A10. When component re-renders unnecessarily

