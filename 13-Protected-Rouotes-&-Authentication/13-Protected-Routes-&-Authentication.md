<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Protected Routes & Authentication in React

## 1. What are Protected Routes?

A Protected route is a page that only logged-in users can access.

Example: 

- Dashboard
- Profile
- Admin page
- Settings
- Settings
- Payment page

If user is not authenticated:

👉 redirect to Login page

## 2. Why Protected Routes are Important

1. Prevent unauthorized access
2. Protect sensitive data
3. Control user flow
4. Improve security
5. Used in all real apps
6. Works with authentication
7. Improves UX
8. Required for dashboards
9. Role-based access
10. Industry standard practice

## 3. Authentication in React

Authentication means:

- checking if user is logged in
- storing login state
- allowing or blocking access

In React (basic level):

- we store auth state using useState
- later this moves to Contex/Redux

## 4. Basic Auth State Setup

    const [isAuth, setIsAuth] = useState(false)

- true -> user logged in
- false -> user logged out

## 5. Protected Route Component 

What this does:

- check auth
- allow access OR redirects

ProtectedRoute.jsx

``` bash
import { Navigate } from 'react-router-dom'

function ProtectedRoute({ isAuth, children }) {
  if (!isAuth) {
    return <Navigate to="/login" replace />
  }
  return children
}

export default ProtectedRoute


```

## 6. App Routing with Protection

App.jsx 

``` bash
import { Routes, Route, Link } from 'react-router-dom'
import { useState } from 'react'
import ProtectedRoute from './ProtectedRoute'

function Home() {
  return <h2>Home</h2>
}

function Dashboard() {
  return <h2>Dashboard (Protected)</h2>
}

function Login({ setIsAuth }) {
  return (
    <button onClick={() => setIsAuth(true)}>
      Login
    </button>
  )
}

function App() {
  const [isAuth, setIsAuth] = useState(false)

  return (
    <>
      <nav>
        <Link to="/">Home</Link> |{' '}
        <Link to="/dashboard">Dashboard</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route
          path="/dashboard"
          element={
            <ProtectedRoute isAuth={isAuth}>
              <Dashboard />
            </ProtectedRoute>
          }
        />
        <Route path="/login" element={<Login setIsAuth={setIsAuth} />} />
      </Routes>
    </>
  )
}

export default App


```

## 7. Logout Functionality

    <button onClick={() => setIsAuth(false)}>Logout</button>

This instantly removes access to protected routes.

## 8. How Redirect Works (Navigate)

    <Navigate to="/login" replace />

- redirects user
- prevents back navigation
- clean UX

## 9. Real-World flow

    User tries to open dashboard
     → Auth check
     → If logged in → show page
     → If not logged in → redirect to login

## 10. Limitaions of This Simple Auth

This is fronted-only auth:

- refresh resets login
- not secure for production

Next steps in real apps:

- JWT tokens
- localStorage
- backend verification
- Context API


## EXERCISE 

## Part 1.

Question: Create a React app that:

- has Home, Login, Profile page
- protects Profile route
- uses useState for auth
- redirects unauthenticated users
- allows login & logout

## Part 2.

Q1.What are protected routes and why are they used?

Q2. How does React Router help implement protected routes?

Q3. Why is fronted-onlt authentication not secure?

## Part 3.

Q1. What is authentication?

Q2. What protects routes?

Q3. Which component redirects users?

Q4. What hook stores auth state?

Q5. Is this sevure for production?

Q6. What happens on logout?

Q7. Which pages are protected?

Q8. What is SPA behavior?

Q9. Can auth be global?

Q10. What comes next for auth?

## Answers

## Part 1.

Answer

``` bash
import { Routes, Route, Link, Navigate } from 'react-router-dom'
import { useState } from 'react'

function Protected({ auth, children }) {
  return auth ? children : <Navigate to="/login" />
}

function Home() {
  return <h2>Home</h2>
}

function Profile({ logout }) {
  return (
    <>
      <h2>Profile</h2>
      <button onClick={logout}>Logout</button>
    </>
  )
}

function Login({ login }) {
  return <button onClick={login}>Login</button>
}

function App() {
  const [auth, setAuth] = useState(false)

  return (
    <>
      <Link to="/">Home</Link> | <Link to="/profile">Profile</Link>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route
          path="/profile"
          element={
            <Protected auth={auth}>
              <Profile logout={() => setAuth(false)} />
            </Protected>
          }
        />
        <Route path="/login" element={<Login login={() => setAuth(true)} />} />
      </Routes>
    </>
  )
}

export default App


```

## Part 2.

A1. Protected routes restrict access to certain pages unless the user is authenticated.
    They are used to protect sensitive data, dashboard, and user specific pages.

A2. React Router allows conditional rendering of reoutes using wrapper components and redirection
    cia Navigate.

A3. Because auth state can be manipulated and is lost on refresh. Secure auth requires backend 
    verification and tokens.

## Part 3.

A1. Verifying user identity

A2. Conditional rendering

A3. Navigate

A4. useState

A5. No

A6. Auth becomes false

A7. Private pages

A8. No reload navigation

A9. Yes (Context)

A10. JWT/Backend
