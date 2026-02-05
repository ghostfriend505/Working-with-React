<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Full React Project (Auth + Router + API + Context + Deplotment)

## What We Are Building 

### Project User Dashboard App

Features: 

- Authentcation (Login/ Logout)
- Protect routes
- Context API for global auth
- Api data fetching
- React Router navigation
- Token handling
- Clean folder structre
- Production-read mindset


## Final Project Folder Structure

    src/
     ├── api/
     │    └── axios.js
     ├── context/
     │    └── AuthContext.jsx
     ├── components/
     │    └── ProtectedRoute.jsx
     ├── pages/
     │    ├── Login.jsx
     │    ├── Dashboard.jsx
     │    └── Home.jsx
     ├── App.jsx
     └── main.jsx


## 1. Auth Context (Global State)

context/AuthContext.jsx

``` bash
import { createContext, useState } from 'react'

export const AuthContext = createContext()

export function AuthProvider({ children }) {
  const [isAuth, setIsAuth] = useState(
    !!localStorage.getItem('token')
  )

  const login = () => {
    localStorage.setItem('token', 'fake-jwt')
    setIsAuth(true)
  }

  const logout = () => {
    localStorage.removeItem('token')
    setIsAuth(false)
  }

  return (
    <AuthContext.Provider value={{ isAuth, login, logout }}>
      {children}
    </AuthContext.Provider>
  )
}

```

## 2 Axios Setup

api/axios,js

``` bash
import axios from 'axios'

const api = axios.create({
  baseURL: 'https://jsonplaceholder.typicode.com'
})

export default api

```

## 3. Protected Route  Component

components/ProtectedRoute.jsx

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

## 4. Pages

pages/Home.jsx

``` bash
function Home() {
  return <h2>Home Page (Public)</h2>
}
export default Home

```

pages/Login.jsx

``` bash
import { useContext } from 'react'
import { AuthContext } from '../context/AuthContext'

function Login() {
  const { login } = useContext(AuthContext)
  return <button onClick={login}>Login</button>
}

export default Login

```

pagese/Dashboard.jsx

``` bash
import { useEffect, useState, useContext } from 'react'
import api from '../api/axios'
import { AuthContext } from '../context/AuthContext'

function Dashboard() {
  const [users, setUsers] = useState([])
  const { logout } = useContext(AuthContext)

  useEffect(() => {
    api.get('/users').then(res => setUsers(res.data))
  }, [])

  return (
    <>
      <h2>Dashboard (Protected)</h2>
      <button onClick={logout}>Logout</button>

      <ul>
        {users.slice(0, 5).map(u => (
          <li key={u.id}>{u.name}</li>
        ))}
      </ul>
    </>
  )
}

export default Dashboard

```

## 5. Routing Setup

App.jsx

``` bash

import { Routes, Route, Link } from 'react-router-dom'
import Home from './pages/Home'
import Login from './pages/Login'
import Dashboard from './pages/Dashboard'
import ProtectedRoute from './components/ProtectedRoute'

function App() {
  return (
    <>
      <nav>
        <Link to="/">Home</Link> |{' '}
        <Link to="/dashboard">Dashboard</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
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
    </>
  )
}

export default App

```

## 6. App Entry 

main.jsx

``` bash
import React from 'react'
import ReactDOM from 'react-dom/client'
import { BrowserRouter } from 'react-router-dom'
import App from './App'
import { AuthProvider } from './context/AuthContext'

ReactDOM.createRoot(document.getElementById('root')).render(
  <BrowserRouter>
    <AuthProvider>
      <App />
    </AuthProvider>
  </BrowserRouter>
)
```

## What This Project Uses 

    | Concept          | Used |
    | ---------------- | ---- |
    | Components       | ✅    |
    | Props & State    | ✅    |
    | Context API      | ✅    |
    | Routing          | ✅    |
    | Protected Routes | ✅    |
    | Auth Flow        | ✅    |
    | API Calls        | ✅    |
    | Hooks            | ✅    |
    | Keys & Lists     | ✅    |

## 🎉 CONGRATULATIONS 🎉

You’ve now completed a FULL MODERN REACT COURSE:

- Beginner → Advanced
- Theory → Practice
- Setup → Deployment
- Code → Architecture

🔥 This is portfolio-level knowledge.
