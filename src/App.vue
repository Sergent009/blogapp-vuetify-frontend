<template>
  <v-app>
    <Navbar @newPost="newPost" />
    <v-main>
      <Dashboard :posts="posts" @updatePost="updatePost" @removePost="removePost" />
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
    },

    updatePost(post){
      let payload = {
        _id: post._id,
        title: post.title,
        author: post.author,
        content: post.content,
        timestamp: post.timestamp
      }

      fetch('http://localhost:3000/api/post/update', {
        method: 'POST',
        headers:{
          "content-type": "application/json"
        },
        body: JSON.stringify(payload)
      })
      .then(data => {
        return data.json()
      })
      .then(json => {
        console.log(json)
      })
    },

    removePost(index){
      fetch('http://localhost:3000/api/post/remove', {
        method: 'POST',
        headers:{
          "content-type": "application/json"
        },
        body: JSON.stringify({_id: this.posts[index]._id})
      })
      .then(data => {
        return data.json()
      })
      .then(json => {
        console.log(json)
      })

      this.posts.splice(index, 1)
    }
  },

  beforeMount(){
    this.getPosts()
  }
};
</script>
