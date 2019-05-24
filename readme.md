# Working with our first project

## Making API request Vue JS Way
1. create a new folder in the pages and name it posts
1. create a new file insie posts and name it index.vue
1. create a template and add the following code below

```
<template>
<div>
    <div>
        <h2>Making API request - the Vue way</h2>
 
    </div>

</div>

</template>

<script>
    export default {
        data() {
            return {
                posts: []
            }
        }
    }
</script>

```

1. now you need to install axios on the project
1. go to learning folder root and type npm install axios
1. write below the script and above the export default the import method.

```
import axios from 'axios'

```

1. write the mounted method after the data method

```
mounted() {

}
```

1. inside the mounted method use the axios to get the fake todo json list service https://jsonplaceholder.typicode.com/todos

```
 axios.get('http://jsonplaceholder.typicode.com/todos/')
 
```
1. add the them promis below axios to get the response data

```
.then(response => {
                console.log(response)
                this.posts = response.data
            })

```

1. add the catch error method to handle the exception if any

```
 .catch(error => {
                console.log(error)
            })

```

1. you can find the final script code should look like this

```
<script>
import axios from 'axios'
    export default {
        data() {
            return {
                posts: []
            }
        },

        mounted() {
            axios.get('http://jsonplaceholder.typicode.com/todos/')
            .then(response => {
                console.log(response)
                this.posts = response.data
            })
            .catch(error => {
                console.log(error)
            })
        }
    }
</script>

```

1. update the template by adding a main container div to wrap evrething and then adding a seperator hr with the following code

```
<hr />
<div class="container">
        <h4 v-for="post in posts" :key="post.id">{{post.title}}</h4>
</div>

```
1. try to explain the v-for and the :key role and what will do
1. check the results the page should load successfully.
1. the final code for the index.vue inside the posts page is the following

```
<template>
<div>
    <div>
        <h2>Making API request - the Vue way</h2>
 
    </div>
<hr />
<div class="container">
        <h4 v-for="post in posts" :key="post.id">{{post.title}}</h4>
</div>

</div>

</template>

<script>
import axios from 'axios'
    export default {
        data() {
            return {
                posts: []
            }
        },

        mounted() {
            axios.get('http://jsonplaceholder.typicode.com/todos/')
            .then(response => {
                console.log(response)
                this.posts = response.data
            })
            .catch(error => {
                console.log(error)
            })
        }
    }
</script>


```


## Making API request using asncData using Nuxt Js

* asyncData() is called every time before loading the component
* use only on nuxt pages not in vue components

* asyncData is called from the server side before the component is mounted
* that's why you dont have access to 'this' keyword inside asyncData()

* this method receives the context object as the first argument,
* you can use it to access core nuxt proerties such as route, store etc

* The result from asyncData will be merged with data. 


## asyncData method runs on both client and server side

1. comment out the scripts inside the index.vue of posts pages and make sure the h2 for loop of posts is commented as well for not displaying any error.
1. create a new script that have the asyncData as following

```
<script>
    export default {
        asyncData(context) {
            console.log(context)
        }
    }
</script>

```

3. shut down the server and run it up again by typing npm run dev
4. refresh the posts page in the browser
5. you can find that you have a huge ogject on the cli, because we console.log the context
6. this meens it is running in the server side.
7. if you open the console.log in the client side at the browser you won't see the context on the client.
8. if you navigate to home page and then back to posts you will noticed that the console.log will display on the client side.
9. this is a proof of concept that asyncData will run on both server side and client side.
10. for the first time it will load from the server side on the initial load, and once you navigate in the page, it will load as a single page application from the client side.
 