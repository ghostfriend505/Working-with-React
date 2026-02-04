<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">


## 1. What is Routing?

Routing means navigating between different pages/vies in an application.

In traditional websites:

- browser requests a new page from server
- full page reload happens

In React:

- page changes without reload
- only components change
- app feels fast

This is called Single Page Application (SPA).

## 2. What is React Router?

React Router is a library that enables client-side routing in React.

It allows:

- multiple pages in SPA
- navigation without reload
- dynamic URLs
- protected routes

React alone cannot handle routing - React Router is required.

## 3. Why React Router is Important

- Enables SPA navigation
- Prevents page reload
- Imporves performance
- Better user experience
- URL-base navigation
- Supports dynamic routes
- Enables nest routes
- Used in real projects
- SEO-friendly with SSR
- Industry standard

## 4. Installing React Router 

``` bash

npm install react-router-dom

```

## 5. Core Components of React Router

    | Component     | Purpose                   |
    | ------------- | ------------------------- |
    | BrowserRouter | Wraps app                 |
    | Routes        | Holds all routes          |
    | Route         | Defines path              |
    | Link          | Navigation without reload |
    | useParams     | Read URL params           |
    | useNavigate   | Programmatic navigation   |

## 6. Basic Setup

``` bash

main.jsx

import React from 'react'
import ReactDOM from 'react-dom/client'
import {BrowserRouter} from 'react-router-dom'
import App from './App.jsx'

ReactDOM.createRoot(document.getElementById('root')).render(
  <BroswerRouter>
    <App />
  </BrowserRouter>
)
```

## 7. Creating Pages

``` bash

src/pages/Home.jsx
function Home() {
  return <h2>Home Page</h2>
}
export default Home

src/pages/About.jsx
function About() {
  return <h2>About Page</h2>
}
export default About

src/pages.Contact.jsx
function Contact() {
  return <h2>Contact Page</h2>
}
export default Contact

```

## 8. Defining Routes

```bash

App.jsx

import { Routes, Route, Link } from 'react-router-dom'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'

function App() {
  return (
    <div>
      <nav>
        <Link to="/">Home</Link> | 
        <Link to="/about">About</Link> | 
        <Link to="/contact">Contact</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </div>
  )
}

export default App

```

## 9. Ling vs <a> Tag

    | <a>          | <Link>     |
    | ------------ | ------------ |
    | Reloads page | No reload    |
    | Slow         | Fast         |
    | Not SPA      | SPA friendly |

## 10. Dynamic Routing (useParams)

Example URL:

    /user/5

``` bash

import { useParams } from 'react-router-dom'

function User() {
  const { id } = useParams()
  return <h2>User ID: {id}</h2>
}

export default User

```

Route:

    <Route path="/user/:id" element={<User />} />

## 11. Programmactic Navigation (useNavigate)

``` bash
import { useNavigate } from 'react-router-dom'

function Login() {
  const navigate = useNavigate()

  return (
    <button onClick={() => navigate('/')}>
      Login
    </button>
  )
}

```

## 12. Summary 

- React Router enables navigation
- BrowserRouter wraps app
- Routes define paths
- Link navigates without reload
- Params handle dynamic URLs

## Exercises

### Part 1.

Question: Create a React app that:

- has Home,About,Profile pages
- user React Router
- uses Link for navigation
- uses dynamic route for Profile (/profile/:name)
- displays URL param

### Part 2. 

Q1. Why do we need React Router in React apps?

Q2. Explain how client-side routing works.

Q3. Explain dynamic routing in React Router

### Part 3. 

Q1. What is SPA?

Q2. Which pakages is used for routing?

Q3. What component wraps routes?

Q4. What replaces <a> in React?

Q5. What hook reads URL params?

Q6. What hook navigates programmatically?

Q7. Does Link reload page?

Q8. What is dynamic routing?

Q9. Which version is used now?

Q10. Why routing is fast?

### Answers

### Part 1.

``` bash
import { Routes, Route, Link, useParams } from 'react-router-dom'

function Home() {
  return <h2>Home</h2>
}

function About() {
  return <h2>About</h2>
}

function Profile() {
  const { name } = useParams()
  return <h2>Profile: {name}</h2>
}

function App() {
  return (
    <>
      <Link to="/">Home</Link> | 
      <Link to="/about">About</Link> | 
      <Link to="/profile/Ujjwal">Profile</Link>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/profile/:name" element={<Profile />} />
      </Routes>
    </>
  )
}

export default App

```

### Part 2.

A1. React Router allows navigation without page reloads, enabling SPA behavior. It improves
    performance, user experience, and allows URL-based navigation.

A2. Clien-side routing changes components based on URL hanges without requesting a new page
    from the server. React Router listen to URL changes and renders matching omponents.

A3. Dynamic routing allows parts of the URL to act as variables. useParams is used to read
    these values and render dynamic content.

### Part 3.

A1. Single Page Application

A2. react-router-dom

A3. BrowserRouter

A4. Link

A5. useParams

A6. useNavigate

A7. No

A8. URL with params

A9. v6

A10. No reload
