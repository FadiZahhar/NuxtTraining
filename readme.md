# Deploying to Firebase

## Deploy Static Site
1. go to the following link and check the available commands https://nuxtjs.org/guide/commands/
2. we will focus with nuxt build and nuxt generate, we will try both of them.
3. we will try the generated deployment (Pre Rendered)
4. first of all we need to run npm run generate.
5. will create a dist folder that have all the html.
6. we need to fix couple of things before deployment .
7. go to store in the index.vue comment the nuxtinitserver of the action since this won't work this will be initiated in the server and need a server side
8. commit the following code in the store
`//async nuxtServerInit({ commit }) {
		//let { data } = await axios.get(
		//	"https://jsonplaceholder.typicode.com/posts"
		//);
		//commit("SET_POSTS", data);
	//}
	 setPosts({ commit }, posts) {
	 	commit("SET_POSTS", posts);
	 }`
9. uncommit the following code in the index.vue posts pages.
`async fetch({store}) {
		let {data} =  await axios.get('https://jsonplaceholder.typicode.com/posts')
		 return {allPosts: data}
		store.dispatch('setPosts', data)
		 },   `
10. after that run the command npm run generate.
11. this will create the dist folder that is ready to be deployed on the static site.
12. this will minified evrething including the html and js.
13. now we can deploy to firebze.

## how to deploy to firebase.
1. google how to do so.
2. install the tools globaly so from any folder you can run the command.
3. once it is done.
4. you need to login to firebase.
5. you can create an account and login to the console.
6. go to your root of the project and write firebase initiated
7. we would like to use only the hosting.
8. create a project from the console and create a new project.
9. use the project from the available question.
10. my public directory is dist
11. do you want to overwrite (no)
12. firebase deploy


# Deploy Single Page application to firebase.
1. the only change we should make is to change the universal mode to single page application in the nuxt.config.js
2. set the mode to 'spa'
3. then use npm run build
4. follow the same steps here.
5. while deploying you need to answer some questinos for firebase to configure as single page applicaiton.
