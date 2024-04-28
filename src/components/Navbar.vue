<template>
  <nav>
    <v-toolbar dark app>
       <v-app-bar-nav-icon />
      <v-toolbar-title class="text-uppercase yellow--text">
        Mannan's <span class="font-weight-light">Mind</span> Admin
      </v-toolbar-title>
        <v-spacer></v-spacer>

      <v-toolbar-items>
        <v-btn outlined color="white">New Post</v-btn>
      </v-toolbar-items>
    </v-toolbar>

    <!-- without persistant, if we click anywhere outside the dialog, the dialog will be closed. -->
    <v-dialog v-model="newPostDialog" persistent max-width="768">
      <v-card>
        <v-card-title class="grey darken-4 white--text headline">
          New Post
        </v-card-title>
        <v-card-text>
          hello, world!
        </v-card-text>
        <v-card-actions class="grey darken-4">
          <v-btn flat color="white darken-4">Close</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="white darken-4">Update</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </nav>
</template>

<script>
export default {
  name: "MyNavbar",
  data(){
    return{
      drawer: false,
      newPostDialog: false,
      newPost: {}
    }
  }
};
</script>

<style>
</style>