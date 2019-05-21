# Creating Pages
1. in the pages folder remove evrething from pages in the index.vue.
2.  write the following in the index.vue
`
<template>
<h1>Hello world</h1>
</template>

`
3. try to explain what you did
4. in the layouts folder open default.vue, and try to explain what is `<nuxt />` tag role (component).
5. remove all styles in the default.vue layouts, and remove the logo.vue component in the components folder since we won't use them.


## creating a new page users.vue
1. create a new file users.vue, you should know on wish folder in nuxt to create this page.
2. create a template and a h1 that have the text of user pages.
3. go to the /users pages of your localhost:3000
4. discove behind the sceens what was happen in checking the .nuxt folder router.js create routes method.


## creating newsted pages
1. website.com/users/id as example
2. simply create a folder called users
3. create index.vue and paste the old user.vue content into the new index.vue
4. create a new file _id.vue in the users folder, this is how you create a nested pages in nuxt.
5. put a template with a div and h2 that have the text This is user's id X
6. it is recomended to have flexibility to create _id folder and inside it to have an index.vue 
7. cut the values in the _id.vue and paste it to _id/index.vue , and then delete the _id.vue
8. test the nested pages, you will see it will be have the same. but now you have more flexibility create more nested pages.

## route parameters
1. use the `{{ $route.params.id }}` instead of X in the  index.vue inside /users/_id folder
2. try to explain what is the method did by testing it  (cast the route parameters and display)
3. 
