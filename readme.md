# Installing and using Plugins
1. google "vue scrollto"
2. install the plugin on the solution folder by typing "npm i vue-scrollto"
3. run the server again by typing "npm run dev"
4. go to your plugins folder, create a new file name it "scrollto.js"
5. open the file and import the following
`import Vue from "vue";
import VueScrollTo from "vue-scrollto"`
6. in the nuxt.config.js go use the plugin globaly by going to plugins section and fill the array.
`plugins: ["@/plugins/scrollto.js"]`
7. go to posts in the pages , index.vue and add the following line below Card
`<Card v-for="post in posts" :key="post.id" :post="post" class="ml-auto mr-auto" />
 <button class="btn btn-danger" v-scroll-to="'body'">Back to Top</button>`


## install vue Cli globaly
1. npm install -g @vue/cli

## install nuxtjs 
1. enter the folder project and white the follow to create a nux app

npx is shipped by default since NPM 5.2.0

npx create-nuxt-app learning

### Fill the questions
 project name
 1. project description
 1. custom ui framework none
 1. ui framework (for now no)
 1. universal (yes)
 1. axios module no
 1. esling no
 1. author name
 choose package manager npm

## run the dev command

1. enter the learning folder in the training project and
1. npm run dev


# Discovering folders in nuxtjs.

1. .nuxt ( a core nuxt js folder )
1. assets uncompile assets
1. components (writing vue js components)
1. Layout (master layouts to use in our entire applications)
1. Middleware ( a certain peace of code that can be run before landing a user to some page, example to restrict a page for not loged in users we use middleware).
1. node_module (include all packages for this applications)
1. pages folder ( dedicated to create nuxt pages )
1. plugins folder ( is a folder that can use third party plugins or create your own plugins and use them in nuxt )
1. static folder ( is for static contect, like fave icon , this folder will not be handeled by webpack.)
1. store (if we create an index.js file in it the vuex store option will be implemented in the nuxt.js framework)
1. nuxt.config.js (is an important file that we will use a lot, the mode export , such universal and spa, also the header page that will apply to all the pages, also can configure each page individually, import css from cdn, can have global css, plugins, modules etc)