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