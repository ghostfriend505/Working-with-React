<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# JWT Authentication & Token Handling in React

## 1. What is Authentication (Recap, Deeper)

Who is the user??

In real apps:

- frontend does NOT decide auth alone
- backend verifies credentials
- backend sends a token
- fronted stores & uses that token

## 2. What is JWT?

JWT = JSON Web Token

A JWT is a singned strong that proves a user is authenticated.

Structure: 

    HEADER.PAYLOAD.SIGNATURE

#### What it contains:

- user id
- role
- expiry time
- issuer info

JWT is:

- stateless
- lightweight
- widely used
- backend verified

## 3. Why Tokens are Used

1. No session storage on server
2. Works with APIs
3. Scales easily
4. Mobile + Web friendly
5. Secure when used correctly
6. Fast authentication
7. Role-based access
8. Industry standard
9. Easy logout
10. Works with SPAs

## 4 Authentication Flow 

    User logs in
     → Server validates credentials
     → Server returns JWT
     → Frontend stores token
     → Token sent with each request
     → Server verifies token

## 5. Where Should Tokens Be Stored?

    | Storage           | Use                              |
    | ----------------- | -------------------------------- |
    | localStorage      | Simple apps                      |
    | sessionStorage    | Short sessions                   |
    | HTTP-only cookies | Most secure (backend controlled) |

For learning -> localStorage

For production -> HTTP -> only cookies

## 6. Storing Token in React (Learning Approach)

    localStorage.setItem('token', jwtToken)

Reading token:

    const token = localStorage.getItem('token')

Removing token (logout)

    localStorage.removeItem('token')

## 7. Login Example (Fronted Simulation)

Login.jsx

``` bash
import axios from 'axios'

function Login() {
  const login = async () => {
    const response = await axios.post('/login', {
      email: 'test@test.com',
      password: '1234'
    })

    localStorage.setItem('token', response.data.token)
  }

  return <button onClick={login}>Login</button>
}

export default Login

```

## 8. Sending Token with API Requests

``` bash
axios.get('/profile', {
  headers: {
    Authorization: `Bearer ${token}`
  }
})

```

Ths proves user is authenticated.

## 9. Axios Interceptors

Insted of adding token every time

axiosInstance.js

``` bash
import axios from 'axios'

const instance = axios.create({
  baseURL: 'https://api.example.com'
})

instance.interceptors.request.use(config => {
  const token = localStorage.getItem('token')
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

export default instance

```

Now all requests automatically include token

## 10. Protecting Routes Using Token

``` bash
function isAuthenticated() {
  return !!localStorage.getItem('token')
}


```

Use in route protection:

``` bash
return isAuthenticated() ? children : <Navigate to="/login" />
```

## Security Notes (Important)

❌ Never trust frontend alone
❌ Never store sensitive data in JWT
❌ Avoid localStorage in production
❌ Always verify token on server

## EXERCISES 

## PART 1

Question: Create a React app that:

- simulates login
- stores JWT in localStorage
- protects dashboard route
- logs out user
- uses Axios interceptor

## PART 2 

Q1. Why is JWT preferred over sessions in SPAs?

Q2. Why should JWT not be trusted on fronted alone?

Q3. Explain Axio interceptors and their benefit.


## PART 3

Q1. What Does JWT stands for?

Q2. Where is token verified?

Q3. Where should token be stored

Q4. What removes token?

Q5. What sends token with request?

Q6. What prevents route access?

Q7. Are JWTs store password?

Q8. Should JWT store password?

Q9. Wat automates headers?

Q10. is fronted auth secure alone?
    
## ANSWERS

## PART 1 

``` bash
import axios from 'axios'
import { Routes, Route, Navigate } from 'react-router-dom'

axios.interceptors.request.use(config => {
  const token = localStorage.getItem('token')
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

function Login() {
  const login = () => {
    localStorage.setItem('token', 'fake-jwt-token')
  }
  return <button onClick={login}>Login</button>
}

function Dashboard() {
  return <h2>Dashboard</h2>
}

function Protected({ children }) {
  return localStorage.getItem('token')
    ? children
    : <Navigate to="/login" />
}

function App() {
  return (
    <Routes>
      <Route path="/login" element={<Login />} />
      <Route
        path="/dashboard"
        element={
          <Protected>
            <Dashboard />
          </Protected>
        }
      />
    </Routes>
  )
}

export default App

```

## PART 2

A1. JWTs are stateless and don not require server-side storage, making them scalable and ideal
    for SPAs and APIs.

A2. Frontend can be manipulated. Tokens mst always be verified on the beckend to ensure 
    authenticity and intergrity.

A3. Axios interceptors automatically attach tokens to requests, reducing repetition and 
    preventing mistakes.

## PART 3 

A1. JSON Web Token

A2. Backend

A3. localStorage

A4. Logout

A5. Authorization header

A6. Protected route

A7. Signed

A8. No

A9. Interceptors

A10. No
