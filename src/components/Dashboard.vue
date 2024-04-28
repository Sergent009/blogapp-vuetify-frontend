<template>
   <v-container fluid class="pa-3">
    <v-layout wrap>
        <v-flex xs12 md8 offset-md2>
            <h1 class="heading">Posts</h1>
        </v-flex>

        <v-flex xs12 md8 offset-md2>
            <v-list two-line class="transparent">
                <v-list-item-title v-for="post in posts.slice((page - 1) * displayAmount, displayAmount * page)" :key="post._id" class="grey darken-4 mb-1">
                    <p class="yellow--text font-weight-bold mb-0">{{post.title}}</p>
                    <v-spacer></v-spacer>
                    <v-btn flat class="success">Update</v-btn>
                    <v-btn flat class="error">Remove</v-btn>
                </v-list-item-title>
            </v-list>
        </v-flex>

        <v-flex  xs12 md8 offset-md2>
            <v-pagination v-model="page" :length="Math.ceil(posts.length / displayAmount)" />
        </v-flex>
    </v-layout>
   </v-container>
</template>

<script>
export default {
    name: 'MyDashboard',
    props: ['posts'],

    data(){
        return{
            page: 1,
            displayAmount: 5
        }
    }
}
</script>

<style lang="stylus" scoped>

</style>