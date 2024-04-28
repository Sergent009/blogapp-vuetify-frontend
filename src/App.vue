<template>
  <v-app>
    <Navbar />
    <v-main>
      <Dashboard :posts="posts" />
    </v-main>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Dashboard from './components/Dashboard.vue'
// import axios from 'axios'

export default {
  name: 'App',

  components: {
    Navbar,
    Dashboard
  },

  data: () => ({
    posts: [
    ]
  }),

  methods:{
    async getPosts(){
      this.posts = await fetch('http://localhost:3000/api/posts/all')
      .then(data => {
        return data.json()
      })
      .then(json => {
        return json.result
      })

      this.posts.sort(function(a, b) {
        if(a.timestamp < b.timestamp){
          return 1
        }
        if(a.timestamp > b.timestamp){
          return -1
        }
        return 0
      })
    },

    newPost(post){
      this.posts.push(post)
      this.posts.sort(function(a, b) {
        if(a.timestamp < b.timestamp){
          return 1
        }
        if(a.timestamp > b.timestamp){
          return -1
        }
        return 0
      })
    }
  },

  beforeMount(){
    this.getPosts()
  }
};
</script>
