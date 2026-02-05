<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Access Tokens & Refresh Tokens

In modern authentication systems, two different tokens are used insted of one. They may look similar,
but they solve two completely different problems.

## Part 1: Access Token (Solving API Access Problem)

### What Problem Does the Access Tojen Solve?

Web applications need a way to:

- prove the user is logged in
- allow access to protected APIs
- avoid sending username/password every time

The access token solves this problem.

### What is an Access Token?

An Access toen is a short-lived token used to:

- aithorize API requests
- identify the user
- greant access to protected resources

It is sent with every APU request.

    Authorization: Bearer ACCESS_TOKEN

### Why Access Tokens are Short-Lived

Access tokens are intentionally short-lived becase:

1. They are sent frequently
2. They can be intercepted
3. They live in fronted memory
4. Short life reduces damage if stolen

Typical expiry: 5-15 min

### Problem with Access Tokens Alone

If we only use access tokens:

- user gets logged out frequently
- bad user experience
- token expiry interrupts usage

So access tokens alone are not enough.

### Summay (Access Tokens)

- Used for API access
- Sent with every request
- Short-lived
- Improves secutrity
- Not meant to keep user logged in forever

## PART 2: Refresh Token (Solving the Session Continuity Problem)

### What Problem Does The Refresh Token Solve?

When an access token expires:

- user should NOT be logged out immediately
- app should renew session silently
- UX should remain smooth

The refresh token solves this problem

### What is a Refresh Token?

A referesh token is a long-lived token use to:

- request a new access token
- keep user logged in
- avoid forcing re-login

### Why Refresh Tokens are Long-Lived

Refresh tokens:

1. Are use rarely
2. Are stored securely (HTTP-only cokkies)
3. Are never exposed to JS (in production)
4. Have limited usage scope

Typica expiry: Days or weeks

### Problem with Refresh Tokens Alone

If we onlt use refresh tokens:

- huge security risk
- token misuse is dangerous
- not desifned for API authorization

So referensh tokens cannot replace accress tokens.

### Summany (Refresh Token)

- Use only to renew access tokens
- Long-lived
- Highly sensitive
- Stored securely
- Never used for API access

### How Both Tokens Work Together (The Real System)

Access tokens and refresh tokens are different, but designed to work as a pair.

    User logs in
     → Server sends Access Token + Refresh Token
     → Access token used for APIs
     → Access token expires
     → Refresh token used to get new access token
     → User continues without logout

This gives:

- Strong security
- smooth user experience

### WHy We Don't use Just one Token?

    | Only Access Token | Only Refresh Token  |
    | ----------------- | ------------------- |
    | Frequent logout   | High security risk  |
    | Bad UX            | Not for APIs        |
    | Needs re-login    | Dangerous if leaked |

Using both = best practice

## One-Line Answer

Access tokens authorize API access, while refresh tokens are used to generate new access
tokens when they expire.

### Simple Analogy 

- Access Token -> entry ticket
- Refresh Token -> renewal slip

You show the ticket often,

You use the renewal slip only when the ticket expires.


### Final Takeaway

- They are different
- They solve diffrent problems
- They are meant to be used together
- This how real-world apps work

