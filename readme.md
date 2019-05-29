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


## Making API request using asyncData using Nuxt Js

* asyncData() is called every time before loading the component
* use only on nuxt pages not in vue components

* asyncData is called from the server side before the component is mounted
* that's why you dont have access to 'this' keyword inside asyncData()

* this method receives the context object as the first argument,
* you can use it to access core nuxt proerties such as route, store etc

* The result from asyncData will be merged with data. 


## asyncData method runs on both client and server side (Proof Of Concept)

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


## Using asyncData
1. try to add the following data() { return posts }

```
<script>
    export default {
        data() {
            return {
                posts: '20 posts'
            }
        },
        asyncData(context) {
            console.log(context)
        }
    }
</script>

```

2. comment the h4 v-for and render the {{posts}} instead.
3. you will see that the hard coded apeared.
4. if we use the asyncData(context) and return as following.

```
<script>
    export default {
        data() {
            return {
                posts: '20 posts'
            }
        },
        asyncData(context) {
            return { posts: '100 posts' }
        }
    }
</script>

```
5. so as you can see that the asyncData method will since to the data and replace the original posts from 20 posts to 100 posts.
6. let us not use context for the moment use axios to get the request with the following url https://jsonplaceholder.typicode.com/todos
7. inport axios and do the following

```
<script>
import axios from 'axios'
    export default {
        data() {
            return posts: ''
        },
        asyncData(context) {
            axios.get('htts://jsonplaceholder.typicode.com/todos')
            .then(res => {
                console.log(res)
            })
        }
    }
</script>

```
8. go to components -> nav.vue and change the home link to nuxt link replace the Nuxt App .navbar-brand class name
```
<nuxt-link to="/" class="navbar-brand">Nuxt App</nuxt-link> 
```
9. instead of console.log(res) replace it with return { posts: res.data}
10. to be able to see the posts results in the front end you need to make sure that you use return axios.get

```
<script>
import axios from 'axios'
    export default {
        data() {
            return posts: ''
        },
        asyncData(context) {
            return axios.get('htts://jsonplaceholder.typicode.com/todos')
            .then(res => {
                return {posts: res.data}
            })
        }
    }
</script>

```
11. after you see all the data, you need to remove {{ posts }} and put again the following code instead.

```

<hr />
<div class="container">
        <h4 v-for="post in posts" :key="post.id">{{post.title}}</h4>
</div>

```
12. you can view the source of the html and you will see it is SEO friendly since it was rendered from the server side.

## async awaite to make API request
1. to spimplify the api request we will use async api.
2. asign the axios.get  with a variable res and use async asyncData() as a method with await keybowrd
3. example 
```
<script>
import axios from 'axios'
    export default {
        data() {
            return posts: ''
        },
        async asyncData() {
            let res = await axios.get('htts://jsonplaceholder.typicode.com/todos')
            return {posts: res.data}
        }
    }
</script>

```

4. we can also distruct the data in another way of typing the code this is an example

```
<script>
import axios from 'axios'
    export default {
        data() {
            return {
                posts: ''
            }
        },
        async asyncData() {
            let {data} = await axios.get('htts://jsonplaceholder.typicode.com/todos')
            return {posts: data}
        },
        head: {
            title: 'List of Posts'
        }
    }
</script>

```

## Vue Component
1. make a reusable component 
2. go to the latest bootsrap link card and take the html code from here https://getbootstrap.com/docs/4.3/components/card/
3. create card.vue in the component folder
4. example

```
<template>
    <div>
        <div class="card" style="width: 18rem;">
        <div class="card-header">Post: {{ post.id }}</div>
        <div class="card-body">
            <h5 class="card-title">{{post.title}}</h5>
        </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: Object
    }
}
</script>

```
5. go to index.vue in posts folder and import the Card from '/@components/Card`

```
import axios from 'axios'
import Card from '@/components/Card'

```

6. above the data() add the components property in the script code
```
<script>
import axios from 'axios'
    export default {
        components: {
            Card
        },
        data() {
            return {
                posts: ''
            }
        },
        async asyncData() {
            let {data} = await axios.get('htts://jsonplaceholder.typicode.com/todos')
            return {posts: data}
        },
        head: {
            title: 'List of Posts'
        }
    }
</script>

```

7. replace the h4 in the index.vue template in the folder posts into the card component.
old code 
```
<div class="container">
<h4 v-for="post in posts" :key="post.id">{{post.title}}</h4>
</div>

```

new code
```
<div class="container row">
<Card v-for="post in posts" :key="post.id" :post="post" class="ml-auto mr-auto" />
</div>

```

## show post by id
1. make each pos by id to open the post.
2. create a folder called _id inside the posts folder
3. create the following template as index.vue inside the _id folder
```
<template>
    <div>
        {{$route.params.id}}
    </div>
</template>

```
4. now you can wrap the nuxt-link inside the post title of the card compopnent to make the link.
```
<h5 class="card-title"><nuxt-link :to="{name : 'posts-id', params:{id: post.id}}">{{post.title}}</nuxt-link></h5>

```

## Getting individual post