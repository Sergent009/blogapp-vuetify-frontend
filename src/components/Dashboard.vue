<template>
  <v-container fluid class="pa-3">
    <v-layout wrap>
      <v-flex xs12 md8 offset-md2>
        <h1 class="heading">Posts</h1>
      </v-flex>

      <!-- <v-flex xs12 md8 offset-md2>
        <v-card class="mx-auto pa-4">
          <v-list two-line class="transparent">
            <v-list-item-title
              v-for="post in posts.slice(
                (page - 1) * displayAmount,
                displayAmount * page
              )"
              :key="post._id"
              class="smoke darken-4 mb-3"
            >
              <p class="black--text font-weight-bold mb-0">{{ post.title }}</p>
              <v-spacer></v-spacer>
              <v-btn icon class="success text-center mr-2" color="black">Upd</v-btn>
              <v-btn icon class="error text-center" color="black">Rem</v-btn>
              <hr>
            </v-list-item-title>
          </v-list>
        </v-card>
      </v-flex> -->

<v-flex xs12 md8 offset-md2>
        <v-card class="mx-auto pa-4" dark>
          <v-list two-line class="transparent">
            <v-list-item
              v-for="(post, index) in posts.slice((page - 1) * displayAmount, displayAmount * page)"
              :key="post._id"
              class="smoke darken-4 mb-3"
            >
              <v-list-item-content>
                <v-list-item-title class="white--text font-weight-bold">{{ post.title }}</v-list-item-title>
              </v-list-item-content>
              <v-list-item-action>
                <v-btn icon class="success text-center mr-6 mb-0" color="black" @click="updatePostDialog(post)">Upd</v-btn>
                <v-btn @click="$emit('removePost', index)" icon class="error text-center mt-0" color="black">Rem</v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list>
        </v-card>
      </v-flex>

      <v-flex xs12 md8 offset-md2>
        <v-pagination
          v-model="page"
          :length="Math.ceil(posts.length / displayAmount)"
        />
      </v-flex>
    </v-layout>

     <v-dialog v-model="updateDialog" persistent max-width="768">
      <v-card>
        <v-card-title class="grey darken-4 white--text headline">
          Update
        </v-card-title>
        <v-card-text>
          <v-container fluid grid-list-xl>
            <v-layout wrap>
              <v-flex xs12 md6>
                <v-text-field label="Title" v-if="currentPost" v-model="currentPost.title" />
              </v-flex>
              <v-flex xs12 md6>
                <v-text-field label="Author" v-if="currentPost" v-model="currentPost.author" />
              </v-flex>
              <v-flex xs12>
                <v-textarea label="Content" v-if="currentPost" v-model="currentPost.content" />
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-text>
        <v-card-actions class="grey darken-4">
          <v-btn @click="updateDialog = !updateDialog" flat color="white darken-4">Close</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="white darken-4" @click="updatePost">Update Post</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>

</template>

<script>
export default {
  name: "MyDashboard",
  props: ["posts"],

  data() {
    return {
      updateDialog: false,
      currentPost: undefined,
      page: 1,
      displayAmount: 5,
    };
  },

  methods:{
    updatePostDialog(post){
      this.currentPost = post
      this.updateDialog = true
    },

    updatePost(){
      this.$emit('updatePost', this.currentPost)
      this.updateDialog = false
    }
  },

}; 
</script>

<style lang="stylus" scoped></style>