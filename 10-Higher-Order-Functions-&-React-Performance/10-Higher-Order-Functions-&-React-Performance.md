<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Higher Order Functions & React Performance

## 1. Performance Measurement in React

#### What is Performance Measurement?

Performance measurement means:

- checking how fast your app renders
- how often components re-renders
- what is slow
- what is unnecessary

React app becomes slow when:

- too many re-renders happen
- heavy calculatioons run again and again
- large list update
- components re-render unnecessarily

Tools to Measure Performance

##### 1. React DevTools Profiler

- shows re-render time
- shows component tree
- shows wasted renders

##### 2. Consle.tom

``` bash
console.time('calc')
//heavy code
console.timeEnd('calc')
```

##### 3. Browser Performance tab

- measure JS execution
- measure paint time
- measure memory

## 2. React Diff Algorithm 

### What is Diff Algorithm??

React does not update the whole DOM.
it compates old Virtual DOM with new Virtual DOM.

This comparison process is called diffing.


How Diffing Works

React uses 3 rules

1. Different element type -> replace whole tree
2. Same type -> update attributes
3. List items -> use key to match items

Example 

``` bash
<ul>
 {items.mao(i =< <li key={i.id}>{i.name}</li>)}
</ul>
```

Key helps React identify which item changed.

## 3. Reconciliation 

What is Reconciliation?

Reaconciliation is the process of:

  | Updating the real DOM based on diffing result.

Flow:

State change
 → Virtual DOM
 → Diffing
 → Reconciliation
 → Real DOM update

Why Reconciliation is Fast

Because:

- only changed nodes update
- batching updates
- optimized algorithm
- avoids full re-rends

## 4. React Performance Optimization Techniques

    | Problem               | Solution        |
    | --------------------- | --------------- |
    | Unnecessary re-render | React.memo      |
    | Heavy calculation     | useMemo         |
    | Function recreation   | useCallback     |
    | Large lists           | virtualization  |
    | Global state          | Context / Redux |
    | Re-render loops       | useEffect deps  |

## 5. Higher Order Functions (HOF) in React

What is Higer Order Function?

A function that:

- takes a function as argument
- returns a function

Example (JS)

``` bash
function withLog(fn) {
  return function () {
    console.log('Calling function')
    fn()
  }
}
```

HOF in React (HOC)

``` bash
function withLoading(Component) {
  return function({ loading, ...props }) {
    if (loading) return <p>Loading...</p>
    return <Component {...props} />
  }
}
```

## 6. React.memo vs HOC (Important)
    
    | React.memo       | HOC               |
    | ---------------- | ----------------- |
    | Optimizes render | Adds behavior     |
    | Component level  | Component wrapper |
    | Performance      | Logic reuse       |

## Exercises 

### Part 1. Code-Based Question

Create a app that:

- measures render time
- uses React.memo
- uses useMemo
- shows how diffing works with key
- logs reconciliation

### Part 2. Long Answer Questions

Q1. Explain how React diffing algorithm improves performance.

Q2. Explain how React diffing algorithm improves performance.

Q3. Why is performance optimization important in large React apps?

Q4. Difference Between React and ReactDOM

### Part 3. Short Answer Questions

Q1. What is diffing?

Q2. What is reconciliation?

Q3. What is React.memo used for?

Q4. What is useMemo used for?

Q5. What is useCallback used for?

Q6. What helps React identify list items?

Q7. What is HOC?

Q8. What tool measures React performance?

Q9. What causes re-render?

Q10. What is Virtual DOM?

## Answers 

### Part 1.

``` bash
import {useState, memo, useMemo} from 'react'

const Item = memo(({ value }) => {
  console.log('Rendered item', value)
  return <li> {value}</li>
})
function App() {
  const [count, setCount] = useState(0)
  const items = useMemo(() => {
    return Array.from({ length: 5 }, (_, i) => i + count)
  }, [count])

  return (
    <div>
      <button onClick={() => setCount(c => c + 1)}>+</button>
      <ul>
        {items.map(i => (
          <Item key={i} value={i} />
        ))}
      </ul>
    </div>
  )
}

export default App
```

### Part 2.

A1. React compares the previous Virtual DOM with the new Virtual DOM 
    instead of updating the real DOM directly. It uses rules to find minimal changes 
    and updates only changed nodes, making UI updates fast and efficient.

A2. Reconciliation is the process of applying differences found by the 
    diffing algorithm to the real DOM. It ensures only necessary updates happen, 
    preventing full page re-renders.

A3. Large apps have many components and frequent updates. Without optimization,
    unnecessary re-renders can slow the app, increase memory usage, and reduce user 
    experience.

A4.

    | Feature                   | React                    | ReactDOM             |
    | ------------------------- | ------------------------ | -------------------- |
    | Purpose                   | Build UI components      | Render UI to browser |
    | Works with                | Components, state, props | Real DOM             |
    | Platform                  | Platform-independent     | Browser-specific     |
    | Package                   | `react`                  | `react-dom`          |
    | Main role                 | Logic & UI structure     | Display UI           |
    | Can work without browser? | Yes (React Native)       | No                   |

Easy to remeber 

- React = Chef (All the COding)
- ReactDOM = Waiter (Serves that code to client)

### Part 3.

A1. Comparing old and new virtual DOM

A2. Updating real DOM based on diff

A3. Prevent re-render

A4.  Cache values

A5. Cache functions

A6.  key

A7. Component wrapper function

A8. Profiler

A9. State/props change

A10. Lightweight copy of DOM
