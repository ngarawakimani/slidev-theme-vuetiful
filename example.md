---
theme: ./
clicks: 1
altCover: true 
---

# Nuxt js 

The intuitive and SEO friendly framework

---
layout: big-points
title: Why nuxt?
titleRow: true
---

- Modular therefore faster development
- Performant
- Easy!

---
layout: big-points
title: Rendering....
titleRow: true
---

- SSR
- Static

<!--
dsfsdfsdfsdfsdfsdfsdffffffsdfsfsdfsdfsfsdf
-->

---
layout: quote
---

# SSR it is...

---
layout: big-points
title: Feature Overview
titleRow: true
---

- Very configurable
- Folder Structure
- Routing
- Async Data
- State management - Vuex
- Deployment

---
title: Configuration
titleRow: true
cols: '2-1'
---

```js
/*
   ** Build configuration
   ** See https://nuxtjs.org/api/configuration-build/
   */
  build: {
    plugins: [
      new webpack.ProvidePlugin({
        // global modules
        $: 'jquery',
        _: 'lodash',
      }),
    ],
    vendor: [],
    transpile: ['@nuxtjs/auth-next', 'tokenByClient'],
    babel: {
      compact: true,
      plugins: ['@babel/plugin-proposal-class-properties', '@babel/plugin-proposal-private-methods'],
    },
  },
```

::right::

## Features

- Server side frameworks
- UI frameworks
- Testing frameworks
- etc ...

---
layout: big-points
title: Folder Structure
titleRow: true
---

- assets
- components
- layouts
- middleware
- pages
- plugins
- static
- store

---
title: Routing
titleRow: true
---

```html
pages/
--| _slug/
-----| comments.vue
-----| index.vue
--| users/
-----| _id.vue
--| index.vue
```

---
titleRow: false
---

```js
router: {
  routes: [
    {
      name: 'index',
      path: '/',
      component: 'pages/index.vue'
    },
    {
      name: 'users-id',
      path: '/users/:id?',
      component: 'pages/users/_id.vue'
    },
    {
      name: 'slug',
      path: '/:slug',
      component: 'pages/_slug/index.vue'
    },
    {
      name: 'slug-comments',
      path: '/:slug/comments',
      component: 'pages/_slug/comments.vue'
    }
  ]
}
```

---
title: Async Data
titleRow: true
---

```html
<template>
</template>
<script>
  export default {
    async asyncData(context) {
      if (context.store.state.associations.forUser === null) {
        await context.store.dispatch('associations/fetchForUser', {
          id: context.$auth.user.id,
          token: context.$auth.strategy.token.get(),
        });
      }
    },
    mounted() {
    },
    data() {
      return {}
    }
  }
</script>
```

---
title: State management - Vuex
titleRow: true
---

```js
import axios from 'axios';

export const state = () => ({
  list: []
})

export const actions = {
  async fetchCountries(context, token) {
    const res = await axios.get(`/country`)
    // Todo - Need some error handling here
    context.commit(`setCountries`, res.data.data)
    return res.data.data
  }
};

export const mutations = {
  setCountries(state, data) {
    state.list = data
  }
};
```

---
layout: big-points
title: Nuxt Auth
titleRow: true
---

```js
<script>
export default {
  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
```

---
layout: outro
---

Thank you for listening!

Questions?
