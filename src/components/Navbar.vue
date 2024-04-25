<template>
  <nav>
    <v-toolbar dark app>
      <!-- <v-toolbar-side-icon /> -->
       <v-app-bar-nav-icon />
      <v-toolbar-title class="text-uppercase yellow--text">
        Mannan's <span class="font-weight-light">Mind</span> Admin
      </v-toolbar-title>
        <v-spacer></v-spacer>

      <v-toolbar-items>
        <v-btn outlined color="white">New Post</v-btn>
      </v-toolbar-items>
    </v-toolbar>
  </nav>
</template>

<script>
export default {
  name: "MyNavbar",
};
</script>

<style>
</style>