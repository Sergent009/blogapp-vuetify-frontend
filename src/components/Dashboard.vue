<template>
   <v-container fluid class="pa-3">
    <v-layout wrap>
        <v-flex xs12 md8 offset-md2>
            <h1 class="heading">Posts</h1>
        </v-flex>

        <v-flex xs12 md8 offset-md2>
            <v-list two-line class="transparent">
                <v-list-item-title v-for="post in posts" :key="post._id" class="grey-darken-4 mb-1">
                    {{post.title}}
                </v-list-item-title>
            </v-list>
        </v-flex>
    </v-layout>
   </v-container>
</template>

<script>
export default {
    name: 'MyDashboard',
    props: ['posts']
}
</script>

<style lang="stylus" scoped>

</style>