# Build Documentation
Look through this documentation to see how the tech stack was built and how to use it.

## Environment
| Software  | Version   |
| --------- | --------- |
| Node      | 10.16.3   |
| NPM       | 6.11.3    |
| @vue/cli  | 4.0.4     |


## Build Steps
1) Install Vue [:link:](https://cli.vuejs.org/guide/installation.html)
    ```bash
    npm install -g @vue/cli
    ```

2) Create a Vue app
    ```bash
    vue create base-vue-vuetify
    ```
   **Options selected:**
    * Manually select features
        * Babel
        * Progressive Web App (PWA) Support
        * Router
        * Vuex
        * CSS Pre-Processors
        * Linter / Formatter
        * Unit Testing
        * E2E Testing
    * Use history mode for router? Y
    * Sass/SCSS (with dart-sass)
    * ESLint + Prettier
    * Lint on save
    * Jest
    * Cypress (Chrome only)
    * In dedicated config files
    
3) Add the Vuetify package
    ```bash
    cd base-vue-vuetify
    vue add vuetify
    ```
    Select the defaut option

4) Base theme adjustments
    * Add font and icon set
        ```bash
        npm install -D @mdi/js
        npm install -D roboto-fontface
        ```
    * Cleanup theme files
        * `src/assets/logo.svg` - **DELETE**
        * `src/views/About.vue` - **DELETE**
        * `src/views/Home.vue`
            ```diff
             <template>
            -  <div class="home">
            -    <img alt="Vue logo" src="../assets/logo.png" />
            -    <HelloWorld msg="Welcome to Your Vue.js App" />
            -  </div>
            +  <HelloWorld msg="Hello World" />
             </template>
            ```
        * `src/components/HelloWorld.vue`
            ```diff
              <template>
             -  <v-container>
             -    <v-layout text-center wrap>
             -      <v-flex xs12>
             -        <v-img
             -          :src="require('../assets/logo.svg')"
             -          class="my-3"
             -          contain
             -          height="200"
             -        ></v-img>
             -      </v-flex>
             -
             -      <v-flex mb-4>
             -        <h1 class="display-2 font-weight-bold mb-3">
             -          Welcome to Vuetify
             -        </h1>
             -        <p class="subheading font-weight-regular">
             -          For help and collaboration with other Vuetify developers,
             -          <br />please join our online
             -          <a href="https://community.vuetifyjs.com" target="_blank"
             -            >Discord Community</a
             -          >
             -        </p>
             -      </v-flex>
             -
             -      <v-flex mb-5 xs12>
             -        <h2 class="headline font-weight-bold mb-3">What's next?</h2>
             -
             -        <v-layout justify-center>
             -          <a
             -            v-for="(next, i) in whatsNext"
             -            :key="i"
             -            :href="next.href"
             -            class="subheading mx-3"
             -            target="_blank"
             -          >
             -            {{ next.text }}
             -          </a>
             -        </v-layout>
             -      </v-flex>
             -
             -      <v-flex xs12 mb-5>
             -        <h2 class="headline font-weight-bold mb-3">Important Links</h2>
             -
             -        <v-layout justify-center>
             -          <a
             -            v-for="(link, i) in importantLinks"
             -            :key="i"
             -            :href="link.href"
             -            class="subheading mx-3"
             -            target="_blank"
             -          >
             -            {{ link.text }}
             -          </a>
             -        </v-layout>
             -      </v-flex>
             -
             -      <v-flex xs12 mb-5>
             -        <h2 class="headline font-weight-bold mb-3">Ecosystem</h2>
             -
             -        <v-layout justify-center>
             -          <a
             -            v-for="(eco, i) in ecosystem"
             -            :key="i"
             -            :href="eco.href"
             -            class="subheading mx-3"
             -            target="_blank"
             -          >
             -            {{ eco.text }}
             -          </a>
             -        </v-layout>
             -      </v-flex>
             -    </v-layout>
             -  </v-container>
             +  <h1>{{ msg }}</h1>
              </template>
              
              <script>
              export default {
             -  data: () => ({
             -    ecosystem: [
             -      {
             -        text: "vuetify-loader",
             -        href: "https://github.com/vuetifyjs/vuetify-loader"
             -      },
             -      {
             -        text: "github",
             -        href: "https://github.com/vuetifyjs/vuetify"
             -      },
             -      {
             -        text: "awesome-vuetify",
             -        href: "https://github.com/vuetifyjs/awesome-vuetify"
             -      }
             -    ],
             -    importantLinks: [
             -      {
             -        text: "Documentation",
             -        href: "https://vuetifyjs.com"
             -      },
             -      {
             -        text: "Chat",
             -        href: "https://community.vuetifyjs.com"
             -      },
             -      {
             -        text: "Made with Vuetify",
             -        href: "https://madewithvuejs.com/vuetify"
             -      },
             -      {
             -        text: "Twitter",
             -        href: "https://twitter.com/vuetifyjs"
             -      },
             -      {
             -        text: "Articles",
             -        href: "https://medium.com/vuetify"
             -      }
             -    ],
             -    whatsNext: [
             -      {
             -        text: "Explore components",
             -        href: "https://vuetifyjs.com/components/api-explorer"
             -      },
             -      {
             -        text: "Select a layout",
             -        href: "https://vuetifyjs.com/layout/pre-defined"
             -      },
             -      {
             -        text: "Frequently Asked Questions",
             -        href: "https://vuetifyjs.com/getting-started/frequently-asked-questions"
             -      }
             -    ]
             -  })
             +  props: {
             +    msg: String
             +  }
              };
              </script>
            ```
        * `src/router/index.js`
            ```diff
                  path: "/",
                  name: "home",
                  component: Home
             -  },
             -  {
             -    path: "/about",
             -    name: "about",
             -    // route level code-splitting
             -    // this generates a separate chunk (about.[hash].js) for this route
             -    // which is lazy-loaded when the route is visited.
             -    component: () =>
             -      import(/* webpackChunkName: "about" */ "../views/About.vue")
                }
              ];
            ```
        * `src/plugins/vuetify.js`
            ```diff
             
             export default new Vuetify({
               icons: {
            -    iconfont: "mdi"
            +    iconfont: "mdiSvg"
               }
             });
            ```
        * `src/store/index.js`
            ```diff
             Vue.use(Vuex);
             
             export default new Vuex.Store({
            +  strict: process.env.NODE_ENV !== "production",
               state: {},
               mutations: {},
               actions: {},
            ```
        * `src/main.js`
            ```diff
             import router from "./router";
             import store from "./store";
             import vuetify from "./plugins/vuetify";
            +import "roboto-fontface/css/roboto/roboto-fontface.css";
             
             Vue.config.productionTip = false;
             
            ```
        * `package.json`
            ```diff
                 "vuex": "^3.0.1"
               },
               "devDependencies": {
            +    "@mdi/js": "^4.5.95",
                 "@vue/cli-plugin-babel": "^4.0.0",
                 "@vue/cli-plugin-e2e-cypress": "^4.0.0",
                 "@vue/cli-plugin-eslint": "^4.0.0",
            ```
            ```diff
                 "eslint-plugin-prettier": "^3.1.0",
                 "eslint-plugin-vue": "^5.0.0",
                 "prettier": "^1.18.2",
            +    "roboto-fontface": "^0.10.0",
                 "sass": "^1.19.0",
                 "sass-loader": "^8.0.0",
                 "vue-cli-plugin-vuetify": "^1.1.0",
            ```
        * `src/App.vue`
            ```diff
             <template>
               <v-app>
            -    <v-app-bar app>
            -      <v-toolbar-title class="headline text-uppercase">
            -        <span>Vuetify</span>
            -        <span class="font-weight-light">MATERIAL DESIGN</span>
            -      </v-toolbar-title>
            -      <v-spacer></v-spacer>
            -      <v-btn
            -        text
            -        href="https://github.com/vuetifyjs/vuetify/releases/latest"
            -        target="_blank"
            -      >
            -        <span class="mr-2">Latest Release</span>
            -      </v-btn>
            -    </v-app-bar>
            -
                 <v-content>
            -      <HelloWorld />
            +      <router-view />
                 </v-content>
               </v-app>
             </template>
            -
            -<script>
            -import HelloWorld from "./components/HelloWorld";
            -
            -export default {
            -  name: "App",
            -  components: {
            -    HelloWorld
            -  },
            -  data: () => ({
            -    //
            -  })
            -};
            -</script>
            ```
        * `public/index.html`
            ```diff
                 <meta name="viewport" content="width=device-width,initial-scale=1.0">
                 <link rel="icon" href="<%= BASE_URL %>favicon.ico">
                 <title>base-vue-vuetify</title>
            -    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900">
            -    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@mdi/font@latest/css/materialdesignicons.min.css">
               </head>
               <body>
                 <noscript>
            ```
5) Make the store modular

    No changes required.  Add store module files to `src/store` and then import them into the root store `src/store/index.js`.  See the [Vuex Module](https://vuex.vuejs.org/guide/modules.html) documentation for further details.  
6) Make the router modular

    No changes required.  Add router segment files to `src/router` and then import them into the router `src/router/index.js`.  Use the spread syntax to add the segments to the router in a nice clean way.
7) Make the layouts dynamic

    These changes will let any route decide which layout to use and also define a default layout.
    * `src/layouts/base.layout.vue` - **NEW**
        ```diff
        +<template>
        +  <v-app>
        +    <v-content>
        +      <router-view />
        +    </v-content>
        +  </v-app>
        +</template>
        ```
    * `src/App.vue`
        ```diff
         <template>
        -  <v-app>
        -    <v-content>
        -      <router-view />
        -    </v-content>
        -  </v-app>
        +  <component :is="layout"></component>
         </template>
        +
        +<script>
        +const DefaultLayout = () => import(/* webpackChunkName: "base" */ "@/layouts/base.layout");
        +export default {
        +  computed: {
        +    layout() {
        +      return this.$route.meta.layout || DefaultLayout;
        +    }
        +  }
        +};
        +</script>
        ```
