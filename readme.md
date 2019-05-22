# Nuxt child Component
create a users.vue in the pages and make a template such this
`
<template>
    <div style="background:red;">
        <h4>You can see me in all users related pages</h4>
    </div>
</template>
`
what we did is we create a template that can be rendered on all users pages, so the folder users, have a template layout inside pages named users.vue


write a Style that have a body of backgorund color azure; in the default vue layouts.



# Using Bootstrap4 and jQuery
there are 2 ways
1. using the CDN 
2. using them as plugin

we will start using the CDN and later in advanced training we will use them as plugin.

1. go to nuxt.config.js
2. in the link array below faveicon style add the following `{ rel: 'stylesheet', href:"https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" }`
3. add the related scripts as an array of object below the link array.
`
    script: [
      {
        src:'https://code.jquery.com/jquery-3.3.1.slim.min.js',
        type: 'text/javascript'
      },
      {
        src:'https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js',
        type: 'text/javascript'
      },
      {
        src:'https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js',
        type: 'text/javascript'
      },
    ]
`

# Creating Navigation
