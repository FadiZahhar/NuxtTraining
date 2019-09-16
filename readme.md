# Installing and using Plugins
1. google "vue scrollto"
2. install the plugin on the solution folder by typing "npm i vue-scrollto"
3. run the server again by typing "npm run dev"
4. go to your plugins folder, create a new file name it "scrollto.js"
5. open the file and import the following
`import Vue from "vue";
import VueScrollTo from "vue-scrollto"`

Vue.use(VueScrollTo);

6. in the nuxt.config.js go use the plugin globaly by going to plugins section and fill the array.
`plugins: ["@/plugins/scrollto.js"]`
7. go to posts in the pages , index.vue and add the following line below Card
`<Card v-for="post in posts" :key="post.id" :post="post" class="ml-auto mr-auto" />
 <button class="btn btn-danger" v-scroll-to="'body'">Back to Top</button>`


## No SSR Component
there are plugins that don't support server side rendering to make it work we need to do the following.
1. isntall it
`npm i vue-select`
2. create a new file in the plugins folder name it 'vueselect.js'
3. import the vue then the library
`import Vue from "vue";
import vSelect from "vue-select";``

4. use the vue component 
`Vue.component("v-select", vSelect);`

5. import the vue globaly on the nuxt.config.js
`plugins: ["@/plugins/scrollto.js",
  {
      src: "@/plugins/vueselect.js",
      ssr: false
    }
  ],
`

6. in the main index.vue pages under the hello world add the following select component
`
<no-ssr>
	  		<v-select v-model="selected" placeholder="Select Category" :options="['foo', 'bar']"></v-select>
	  	</no-ssr>

`

7. the full index.vue should be like that including the script and a div container for not making errors.
`<template>
	<div>
		<h1>hello world</h1>
		<no-ssr>
	  		<v-select v-model="selected" placeholder="Select Category" :options="['foo', 'bar']"></v-select>
	  	</no-ssr>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				selected: ''
			}
		}
	}
</script>`

### notes
this component works on the client side this is we will put <no-ssr> to make it work. also we set the ssr to false in the nux.config.js as an object format.


## Nuxt server init method
this method can be used in the nux view store.
this method can get initialized on the server side and run before the client can be rendered and delivered on the client side.
`
// actions
export const actions = {
	async nuxtServerInit({ commit }) {
		let { data } = await axios.get(
			"https://jsonplaceholder.typicode.com/posts"
		);
		commit("SET_POSTS", data);
	}
	// setPosts({ commit }, posts) {
	// 	commit("SET_POSTS", posts);
	// }
};
`

don't forget to import the axios to the index store and put it at the top.
import axios from "axios";



## Applying transitions
you can apply transition in the nuxt.config.js in the css section such this.
`css: ["@/assets/styles/main.css"],
  transition: {
    name: "fade",
    mode: "out-in"
  },`
  
  in the main.css style on the assets add the following below the .jumbotron code.
  
 `.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
	opacity: 0;
}
`
