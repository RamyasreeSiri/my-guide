# Next.js

to checkout <https://www.npmjs.com/package/react-markdown> & <https://www.npmjs.com/package/markdown-navbar>

## Notes

### what is [nvm](https://github.com/nvm-sh/nvm) an n[https://github.com/tj/n] used for?

nvm allows you to quickly install and use different versions of node via the command line.

Example:

```bash

$ nvm use 16
Now using node v16.9.1 (npm v7.21.1)
$ node -v
v16.9.1
$ nvm use 14
Now using node v14.18.0 (npm v6.14.15)
$ node -v
v14.18.0
$ nvm install 12
Now using node v12.22.6 (npm v6.14.5)
$ node -v
v12.22.6

```

> **Note:** only works in POSIX-compliant shell (sh, dash, ksh, zsh, bash), in particular on these platforms: unix, macOS, and windows WSL(Windows Subsystem for Linux).

n – Interactively Manage Your Node.js Versions

```bash

$ n 10.16.0
Now Node 10.16.0 version is installed
$ n
  node/4.9.1
ο node/8.11.3
  node/10.15.0
Shows a list of Downloaded Node version
Select using up and down arrows

```

> **Note:** n is supported on macOS, Linux, including with Windows Subsystem for Linux, and various other unix-like systems.

### What is **yarn**?

[Yarn](https://yarnpkg.com/) is a package manager.

Install using `$ npm install -g yarn` and update it to version greater than 2 `$ yarn set version berry`.

### What is JAMStack?

### What is Next.js?

The React framework for production
some features include:

- Dev build system
- Production build system
- hybrid(build time), static & server rendering,
- TypeScript support,
- smart bundling,
- route pre-fetching,
- Built in CSS & SASS support
- API routes and more

> Next.js is a full-stack framework, by default, it needs to be hosted on a platform that supports Node.js

### When to use Next.js?

**Do you only need a single page app**
Use Create React App
**Do you need a static site, like a blog, that's also SPA?**
Use Next.js or Gatsby
**Need SSR, an API and all the above?**
Use Next.js

### What are the commands `next`, `next build`, `next start` do?

`next` Will start Next.js in dev mode with hot reloading.

`next build` Will build your project and ready it for production.

`next start` Will start your built app, used in production.

### Routing in Next.js

- The router will automatically route files named index to the root of the directory.
`pages/index.js → /`
`pages/blog/index.js → /blog`
- Each file created under /pages or /src/page will act as an individual route
- dynamic routing has the filename as [parametername] and it can be access via next/router page
  
```jsx

import React from 'react';
import { useRouter } from 'next/router';

// file => /notes/[is].jsx
// route => /notes/1

const Page = () => {
  const router = useRouter();
  const { id } = router.query;


  return <h1>Note page {id}</h1>; // Note page 1
}
export default Page;

```

#### dynamic routing

- with catch-all routes has filename as /notes/[...params] and route as /notes/1/2/3
- optional catch-all routes has filename /notes/[[...params]] and route as /note, /notes/1, /notes/1/2/3

```jsx

import React from 'react';
import { useRouter } from 'next/router';

// file => /notes/[...params].jsx
// route => /notes/1

const Page = () => {
  const router = useRouter();
  const { id } = router.query;


  return <h1>Note page {id}</h1>; // Note page 1
}
export default Page;
```

> Predefined routes take precedence over dynamic routes, and dynamic routes over catch all route

### Navigation in Next.js

- There Link component allows you to do client-side routing. For linking to another site you should just use an a tag instead.

- The href prop takes a page name as it is in the pages directory. For dynamic routes, you will need the as prop as well.

```jsx

<Link href="/user/[id].js" as={`/user/${user.id}`}>
  <a>user</a>
</Link>
```

#### Programmatic navigation

- Can be don using useRouter().push()

```jsx
import React from 'react'
import { useRouter } from 'next/router'

export default () => {
  const router = useRouter()
  const id = 2

  return (
    <div>
      <button onClick={e => router.push('/')}>
        Go Home
      </button>

      <button onClick={e => router.push('/user/[id]', `/user/${id}`)}>
        Dashboard
      </button>
    </div>
  )
}
```

### Styling

- Styles files can't be imported directly in any component(.css file can't be imported), only css modules can be used(.module.css) can be used.

- Global styles can be declared in `./pages/_app.js` file(.css file can be imported here)

### Config

- Custom advanced configuration of Next.js, you can create a `next.config.js` file at root folder
- Can add ENV variables and extend webpack configuration
- We can add plugins for getting pre-defined configuration

### API Route

- Files defined under `./pages/api/` are considered as API Route, and are executed as API handlers
- Server side code doesn't get send to client

```js

// A handler looks like this

// pages/api/data.js
// route => /api/data

export default (req, res) => {
  res.statusCode = 200
  res.setHeader('Content-Type', 'application/json')
  res.end(JSON.stringify({ message: 'hello' }))
}

```

### Fetching Data

- Fetch the data client-side in react the same way we do in (SPA). Hooks, fetch, etc.

> 👍🏾  **tip**: Next.js injects fetch into your environment.
> 👍🏾  **tip**: Checkout [swr](https://swr.vercel.app/) and [react-query](https://react-query.tanstack.com/) for your client side data fetching needs.

- Fetching data ahead of time, following methods can be used which are for prerendering pages,
~~following~~ methods are executed in server and can not be defined in client components or for client side data fetching

  `getStaticProps`
  `getStaticPaths`
  `getServerSideProps`

#### When to use what

- Do you need data at runtime but don't need SSR? Use client-side data fetching.

- Do you need data at runtime but do need SSR? Use getServerSideProps

- Do you have pages that rely on data that is cachable and accessible at build time? Like from a CMS? Use getStaticProps

- Do you have the same as above but the pages have dynamic URL params? Use getStaticProps and getStaticPaths

> ⚠️   **warning**: Don't use getServerSideProps unless absolutely necessary. Because it computes on every requests, it can be slow.

### SSR

<https://production-grade-nextjs.vercel.app/>
<https://hendrixer.github.io/nextjs-course/>
<https://github.com/hendrixer/production-grade-nextjs>
