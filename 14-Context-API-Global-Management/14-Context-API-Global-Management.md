<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Context API & Global State Management in React

## What is Global State?

Global state is data that needs to be accessed by multiple components at different levels of the app.

Example:

- logged-in user
- theme (dark/light)
- language
- cart items
- authentication status

Passing such data via props becomes messy.

This problem is called prop drilling.

## What is Prop Drilling?

Prop drilling means:

- passing props through components that don't need them
- unnecessary coupling
- unreadable code

Example:

    App -> Layout -> Sidebar -> Profile

Context API removes this problem.

## 3. What is Context API?

Context API allows you to:

- create shared data
- provide it at a high level
- consume it anywhere in the component tree

In simple words 

Context is a global storage build into React.

## 4. When Should You Use Context?

Use Context when:

1. Same data is needed in many components
2. Prop drilling becomes annoying
3. Data changes over time
4. App has authentication or themes

Do Not use Context for:

- small, local state
- frequently changing values unnecessarily

## 5. Core Parts of Conntext API
    
    | Part          | Purpose        |
    | ------------- | -------------- |
    | createContext | Create context |
    | Provider      | Provide data   |
    | useContext    | Consume data   |

## 6. Creating Context 

context/AuthContext.jsx

``` bash
import { createContext, useState } from 'react'

export const AuthContext = createContext()

export function AuthProvider({ children }) {
  const [isAuth, setIsAuth] = useState(false)

  const login = () => setIsAuth(true)
  const logout = () => setIsAuth(false)

  return (
    <AuthContext.Provider value={{ isAuth, login, logout }}>
      {children}
    </AuthContext.Provider>
  )
}


```

## 7. Providing Context to App

main.jsx

``` bash
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import { AuthProvider } from './context/AuthContext'

ReactDOM.createRoot(document.getElementById('root')).render(
  <AuthProvider>
    <App />
  </AuthProvider>
)


```

## 8. Consuming Context Anywhere 

components/Navbar.jsx

```bash
import { useContext } from 'react'
import { AuthContext } from '../context/AuthContext'

function Navbar() {
  const { isAuth, logout } = useContext(AuthContext)

  return (
    <div>
      {isAuth && <button onClick={logout}>Logout</button>}
    </div>
  )
}

export default Navbar


```

## 9. Using ontext in Protected Routes 

ProtextedRoute.jsx

``` bash
import { Navigate } from 'react-router-dom'
import { useContext } from 'react'
import { AuthContext } from '../context/AuthContext'

function ProtectedRoute({ children }) {
  const { isAuth } = useContext(AuthContext)

  return isAuth ? children : <Navigate to="/login" />
}

export default ProtectedRoute


```

## 10. Context + Router Example (App.jsx)

``` bash
import { Routes, Route } from 'react-router-dom'
import { useContext } from 'react'
import { AuthContext } from './context/AuthContext'
import ProtectedRoute from './components/ProtectedRoute'

function Login() {
  const { login } = useContext(AuthContext)
  return <button onClick={login}>Login</button>
}

function Dashboard() {
  return <h2>Dashboard</h2>
}

function App() {
  return (
    <Routes>
      <Route path="/login" element={<Login />} />
      <Route
        path="/dashboard"
        element={
          <ProtectedRoute>
            <Dashboard />
          </ProtectedRoute>
        }
      />
    </Routes>
  )
}

export default App


```

## 11. Context vs Props vs Redux

      | Feature     | Props          | Context     | Redux      |
      | ----------- | -------------- | ----------- | ---------- |
      | Scope       | Local          | App-level   | Global     |
      | Complexity  | Low            | Medium      | High       |
      | Boilerplate | None           | Low         | High       |
      | Use case    | Few components | Medium apps | Large apps |

## Common Mistakes 

❌ Overusing context

❌ Putting everything in one context

❌ Using context for fast-changing state

❌ Forgetting provider wrap

## EXERCISE

## PART 1

Question: Create a React app that:

- Uses Context API
- stores theme (dark/light)
- allows toggle theme
- consumesn context in multiple components
- avoids prop drilling

## PART 2

Q1. Why is Context API needed in React?

Q2. Explain how Context API works internally

Q3. When should you NOT use Context API?


## PART 3

Q1. What problem does context solve?

Q2. Which function creates context?

Q3. How do you comsume context?

Q4. What provides context values?

Q5. Is context global?

Q6. Does context cause re-renders?

Q7. Should context replace Redux?

Q8. Where is Provider placed?

Q9. Can context store functions?

Q10. Is context build-in?
    
## Answers 

## Part 1 

``` bash
import { createContext, useContext, useState } from 'react'

const ThemeContext = createContext()

function ThemeProvider({ children }) {
  const [dark, setDark] = useState(false)

  return (
    <ThemeContext.Provider value={{ dark, toggle: () => setDark(d => !d) }}>
      {children}
    </ThemeContext.Provider>
  )
}

function Button() {
  const { toggle } = useContext(ThemeContext)
  return <button onClick={toggle}>Toggle Theme</button>
}

function App() {
  const { dark } = useContext(ThemeContext)

  return (
    <div style={{ background: dark ? '#000' : '#fff', height: '100vh' }}>
      <Button />
    </div>
  )
}

export default function Root() {
  return (
    <ThemeProvider>
      <App />
    </ThemeProvider>
  )
}


```

## Part 2 

A1. Context API is needed to share data globally without passing props through every components,
   avoiding prop drilling and improving maintainability.

A2.  Context creates a shared store, Provider supplies values, and consumers access 
      values using useContext. When value changes, subscribed components re-render.

A3. Context creates a shared store, Provider supplies values, and consumers access values
    using useContext. When value changes, subscribed components re-render.
    
## Part 3 

A1. Prop drilling

A2. createContext

A3. useContext

A4. Provider

A5. Yes (within tree)

A6. Yes

A7. No

A8. High in tree

A9. Yes

A10. Yes
