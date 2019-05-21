# Starng installing nuxtjs
check you node version node -v

## install vue Cli globaly
npm install -g @vue/cli

## install nuxtjs 
enter the folder project and white the follow to create a nux app

npx is shipped by default since NPM 5.2.0

npx create-nuxt-app learning

### Fill the questions
 project name
 - project description
 - custom ui framework none
 - ui framework (for now no)
 - universal (yes)
 - axios module no
  - esling no
  - author name
 choose package manager npm

## run the dev command

enter the learning folder in the training project and

npm run dev


# Discovering folders in nuxtjs.

.nuxt ( a core nuxt js folder )

assets uncompile assets

components (writing vue js components)

Layout (master layouts to use in our entire applications)

Middleware ( a certain peace of code that can be run before landing a user to some page, example to restrict a page for not loged in users we use middleware).

node_module (include all packages for this applications)

pages folder ( dedicated to create nuxt pages )

plugins folder ( is a folder that can use third party plugins or create your own plugins and use them in nuxt )

static folder ( is for static contect, like fave icon , this folder will not be handeled by webpack.)

store (if we create an index.js file in it the vuex store option will be implemented in the nuxt.js framework)


nuxt.config.js (is an important file that we will use a lot, the mode export , such universal and spa, also the header page that will apply to all the pages, also can configure each page individually, import css from cdn, can have global css, plugins, modules etc)
