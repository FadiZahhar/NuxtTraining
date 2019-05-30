# Activate Vues store
if you need to store some data that can be used in multiple parse of applicaiton
you can find the store folder that can be used to create your file 
1. you need to install the vue chrome extension.
2. if you opened the vue tab in developer console you can find components vuex events and refresh.
3. click on vuex you will noticed that no vuex store detected.
4. go to store folder and create index.php this will activate the vuex, if you can't see it you need to restart the server so you will see base state


# Loading images from assets folder
1. before you created a folder called styles and inside have main.css
2. in case these was not created kindly make sure you have the following structure
3. assets/styles/main.css
4. this is the code in the main.css
```
.jumbotron {
    border-radius: 0px;
    background-image: url("https://cdn.pixabay.com/photo/2016/09/04/20/09/mountains-1645078__480.jpg");
    height: 300px;
    background-size: cover;
}

```
5. copy the image url https://cdn.pixabay.com/photo/2016/09/04/20/09/mountains-1645078__480.jpg by putting it in the browser and save it to static folder in nuxt project.
6. name it mountains.jpg
7. replace the background image on the following code
```
.jumbotron {
    border-radius: 0px;
    background-image: url("/moutains.jpg");
    height: 300px;
    background-size: cover;
}

```
# Setup our vuex store
1. create a store in index.vue as following
```
// create a store
export const state = () => ({
    posts: {}
});

// getters
export const getters = {
    posts(state) {
        return state.posts
    }
};

// mutations
export const mutations = {
    SET_POSTS(state, posts) {
        state.posts = posts
    }
};

// actions
export const actions = {
    setPosts({commit}, posts}) {
        commit("SET_POSTS", posts);
    }
};

```

# populate vuex store
1. we can dispatch one of these actions to get posts in our state
2. go to index.vue in post folder and comment the return {post: data} and replace it store.dispatch('setPosts',data);
3. the code will look like this
```
<script>
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
            // return {posts: data}
            store.dispatch('setPosts',data)
        },
        head: {
            title: 'List of Posts'
        }
    }
</script>

```
4. you can try the console to check that the posts are stored in store.
5. what happened behind the sceen that the setPosts, we commit the method mutations that muted the state SET_POSTS that populated the posts;

# accessing data from vuex store
1. create a computed property below the data() to load all the posts.
```
 data() {
            return {
                posts: ''
            }
        },
 computed: {
     allPosts() {
         return this.$store.getters.posts
     }    
 },

```
2. check the console for the store.
3. in breif we pushed all the data , and in computed method we returned the this.$store.getters.posts

# another method to return all posts
1. insted of the return this.$store.getters.posts, we can import {mapGetters} from 'vuex'
```
import {mapGetters} from 'vuex'

```
2. and in the computed properly we can write the following.
```

...mapGetters(['posts',['blogs','it is an array of]])

```
3. if you decide to use this method, you need to make sure that the return data type is not Posts, since it will have a conflict name , since it is already defined.
4. what you need to do is to replace the return data from Posts:'' to AllPosts.

# using nuxt fetch method
asyncData will sync automatically to all data we have, however if you are not planing to synch the data then you can use fetch
```
async fetch({store}) {
    let {data} = await axios.get('https://jsonplaceholder.typicode.com/posts')
    // return {allPosts: data}
    store.dispatch('setPosts', data)
}
```