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

4. now you need to install axios on the project

5. go to learning folder root and type npm install axios

6. write below the script and above the export default the import method.

```
import axios from 'axios'

```

7. write the mounted method after the data method

```
mounted() {

}
```

8. inside the mounted method use the axios to get the fake todo json list service https://jsonplaceholder.typicode.com/todos

```
 axios.get('http://jsonplaceholder.typicode.com/todos/')
 
```
9. add the them promis below axios to get the response data

```
.then(response => {
                console.log(response)
                this.posts = response.data
            })

```

10. add the catch error method to handle the exception if any

```
 .catch(error => {
                console.log(error)
            })

```

11. you can find the final script code should look like this

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

12. update the template by adding a main container div to wrap evrething and then adding a seperator hr with the following code

```
<hr />
<div class="container">
        <h4 v-for="post in posts" :key="post.id">{{post.title}}</h4>
</div>

```
13. try to explain the v-for and the :key role and what will do

14. check the results the page should load successfully.

15. the final code for the index.vue inside the posts page is the following

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




