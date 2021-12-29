# FAQ, HOWTO STATIC SITE TOOL

A simple static site for serving faq's and howto markdown docs

# TODO's

- [ ] Continue Clean up ui
- [ ] Add Howtos to Search
- [ ] close search on click outside with results


### Built With
- Nuxt.js (in "universal mode", where both SEO and speed is great)
- Vue 2
- Vuex (supported by adding to `/store`, but not implemented)
- PostCSS (no SCSS)
- Tailwind



# BASED FROM 
**[GITHUB ](https://github.com/Knogobert/ntn-boilerplate)**
**[Live Demo](https://ntn-boilerplate.netlify.app/)**
Originally based on [Henry Desroches' nuxt-netlify-cms-starter](https://github.com/xdesro/nuxt-netlify-cms-starter).



## Project commands

1. 📦 Install dependencies.

```bash
npm install
```

2. 🏗 Run the project for local dev. This will start a hot-reloading server at `localhost:3000`.

```bash
npm run dev
```

3. 🌌 Build the app for server-side rendered deployment. See more about **Universal SSR** in the [Nuxt.js docs](https://nuxtjs.org/guide#server-rendered-universal-ssr-).

```bash
npm run build

# And to serve that deployment...
npm run start
```

4. ⚡️ Generate a fully pre-rendered static site. See more [in the docs](https://nuxtjs.org/guide#static-generated-pre-rendering-).

```bash
npm run generate
```

