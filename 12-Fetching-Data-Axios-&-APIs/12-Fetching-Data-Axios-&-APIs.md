<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

## 1. What is an API?

An API (Application Programming Interface) is a way for two applications to communicate.

In simple terms:

- Frontend (React) -> ask for data
- Backend (server) -> sends data (usually JSON)

Example

- Get users
- Get products
- Login users
- Fetch posts

## 2. Why Data Fetching is Important

Almost every real app needs data:

1. User data
2. Product lists
3. Dashboards
4. Authentication
5. Search results
6. Notidications
7. Analytics
8. Forms submission
9. Admin panels
10. Mobile & web sync

Without API cakks, REact apps are incomplete.

## 3. Fetch vs Axios 

    | Fetch                 | Axios                 |
    | --------------------- | --------------------- |
    | Built-in              | External library      |
    | More code             | Cleaner syntax        |
    | No auto JSON          | Auto JSON             |
    | Manual error handling | Better error handling |
    | No interceptors       | Supports interceptors |

## 4. Intalling Axios

    npm install axios

## 5. Basic Axios GET Request

Example API 

    https://jsonplaceholder.typicode.com/users

``` bash

App.jsx

import { useEffect, useState } from 'react'
import axios from 'axios'

function App() {
  const [users, setUsers] = useState([])
  const [loading, setLoading] = useState(true)

  useEffect(() => {
    axios
      .get('https://jsonplaceholder.typicode.com/users')
      .then(res => {
        setUsers(res.data)
        setLoading(false)
      })
      .catch(err => {
        console.log(err)
        setLoading(false)
      })
  }, [])

  if (loading) return <p>Loading...</p>

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  )
}

export default App
```

## 6. Why useEffect is Used for API calls

API calls are:

- side effects
- asynchronous
- should not run on every render

useEffects(() => {}, []) ensures:

- API is called once
- component doesn't loop
- performance stays good

## 7. Handling Errors Properly

``` bash

.catch(error => {
  console.error('Error fetching data:', error)
})

```
Always handle errors to avoid crashes.

## 8. Loading State

Without loading state:

- UI shows empty screen
- bas UX

With loading state:

- user knows data is coming

## 9. POST Request Example

``` bash
axios.post('https://jsonplaceholder.typicode.com/posts', {
  title: 'Hello',
  body: 'This is a post',
  userId: 1
})
```

Used for:

- forms
- login
- signup
- submit data

## 10. Fetching Data on Button Click

``` bash
const fetchData = () => {
  axios.get(url).then(res => setData(res.data))
}

<button onClick={fetchData}>Fetch</button>

```

## Common Mistakes 

❌ API call inside render

❌ No error handling

❌ No loading state

❌ Missing dependency array

❌ Using index as key

## Exercises

## Part 1.

Question: Create a React app that:

- fetch posts from an API
- uses Axios
- shows loading text
- handles errors
- display list with keys

## Part 2

Q1. Why is Axios preferred over fetch?

Q2. Why should API calles be made inside useEffect?

Q3. Explain the importance of loading and error states.

## Part 3

Q1. What is Axios?

Q2. Which hool is used for API calls?

Q3. Why use loading state?

Q4. What format do APIs return?

Q5. Which method fetches data?

Q6. Which method sends data?

Q7. What is a side effect?

Q8. Where should API calls not be made?

Q9. What handles errors in Axios?

Q10. What identidies list items?

## Answers

## Part 1

``` bash
import { useEffect, useState } from 'react'
import axios from 'axios'

function App() {
  const [posts, setPosts] = useState([])
  const [loading, setLoading] = useState(true)
  const [error, setError] = useState(null)

  useEffect(() => {
    axios
      .get('https://jsonplaceholder.typicode.com/posts')
      .then(res => {
        setPosts(res.data.slice(0, 5))
        setLoading(false)
      })
      .catch(err => {
        setError('Failed to fetch data')
        setLoading(false)
      })
  }, [])

  if (loading) return <p>Loading...</p>
  if (error) return <p>{error}</p>

  return (
    <ul>
      {posts.map(post => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  )
}

export default App

```

## Part 2:

A1. Axios provides cleaner syntax. automatic JSON parsing, better error handling, request 
    cancellation. and interceptors, making it more suitable for large applications.

A2. Because API calls are side effects. useEffect contols when they rin and prevents indinite 
    loops and innecessary re-fetching.

A3. Loading states improve user experience by showing progress, and error states prevent crashes
    and inform users when something goes wrong.

## Part 3: 

A1. HTTP client library

A2. useEffect

A3 Better UX

A4. JSON

A5. GET

A6. POST

A7. External operation

A8. Render body

A9. catch

A10. Key

