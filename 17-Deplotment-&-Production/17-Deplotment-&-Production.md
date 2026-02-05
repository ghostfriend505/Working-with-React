<img src = "https://github.com/ghostfriend505/Working-with-React/blob/main/React%20Intro.png">

# Deplotment & Production Build

## 1. What is Deployment?

Deployment means:

- converting your REact app into optimized files
- uploading them to a server
- making the app accessible via a URL

After deployment:

- anyonce can access your app
- no Node server is required for fronted
- app runs fast and optimized

## 2. Development vs Production 
    
    | Development         | Production         |
    | ------------------- | ------------------ |
    | Large files         | Optimized files    |
    | Debug tools         | No debug tools     |
    | Slow                | Fast               |
    | Source code visible | Bundled & minified |
    | For learning        | For users          |

We never deploy dev code

## 3. What is build in Vite?

A build is the process of:

- bundling files
- minifying JS/CSS
- removing unused code
- optimizing assets

In Vite:

      npm run build

This creates a dist/ folder.

## 4. What is inside dist/ Folder?

    dist/
     ├── assets/
     │    ├── index-xxxxx.js
     │    ├── index-xxxxx.css
     └── index.html

This is your final app

You deploy this folder - not src.

## 5. How Vite Build Works (Internally)

    src code
     → Vite bundler
     → Tree shaking
     → Minification
     → Hashing
     → dist folder

Hashing helps with:

- cache control
- faster loading
- updates without conflocts

## Testing Build Locally

Before deploying 

    npm run preview

This runs the production build locally.

## 7. Popular Deplotment Platforms

    | Platform     | Best For         |
    | ------------ | ---------------- |
    | Netlify      | Beginners        |
    | Vercel       | React / Next     |
    | GitHub Pages | Simple demos     |
    | Firebase     | Google ecosystem |

We'll focus on Netlify & Vercel.

## 8. Deploying to Netlify 

Option 1. Drag & Drop

1. Run npm run build
2. Open netlify
3. Drag dist/ folder
4. Done

Option 2: Github Intergration (Recommended)

- Push code to GitHub
- Connect repo to Netlify
- Set build command:

      npm run build

- Set publish directory:

      dist

  ## 9. Deploying to Vercel

      npm install -g vercel
      vercel

## 10. Enviroment Variables (Production)

In Vite:

      VITE_API_URL=https://api.example.com

Usage:

    import.meta.env.VITE_API_URL

Never expose secrets.

## Common Deployment Issues

❌ Blank page → wrong base path

❌ 404 on refresh → missing SPA redirect

❌ Env not working → wrong prefix

❌ Build fails → dependency errors

## SPA Redirect Fix 

For Netlify:

Create _redirects file in public/:

    /*    /index.html   200


## EXERCISE 

## PART 1 

Questionn: Explain and demonstrate how to:

- build a Vite React app
- test production build locally
- deploy it to Netlify
- fix SPA routing issue

## PART 2

Q1. Why should we build before deploying?

Q2. What is the role of the dist folder?

Q3. Why does SPA need redirect confifuration?
   

## PART 3 

1. Which command builds Vite app?

2. Which folder is deployed?

3. Whcih command previews build?

4. Is Node required in production?

5. What prefix env cars need?

6. Which file fixex routhing?

7. Best platform for behinners?

8. Does build include source code?

9. Is dev mode deployed?

10. What is hashing used for?

## ANSWERS

## PART 1 

Answer 

    npm run build
    npm run preview

Deplot dist/ folder to Netlify.

Add _redirects file for routing support.

## PART 2

A1. Because production builds are optimized, smaller, faster, abd secure. Development builds
    are slow and unsafe for users.

A2. It contains the final optimized file that browsers understand and is the only folder deployed.

A3. Because routing happens client-side. Server must redirect all routs to index.html. 

## Part 3

A1. npm run build

A2. dist

A3. npm run preview

A4. No

A5. VITE_

A6. _redirects

A7. Netlify

A8. No

A9. No

A10. Cache control
