<template>
<div v-if="posts.length > 0">
    <h3>List of posts</h3>
        <post-item v-for="post in posts" 
            :post="post" 
            :key="post.id"
            @remove="$emit('remove', post)"
         />
</div>
<div v-else style="color: red">
    <h3>The list of posts is empty</h3>
</div>
</template>

<script>
import PostItem from "@/Components/PostItem.vue";

export default {
    components: {
        PostItem
    },
    props: {
        posts: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>

</style>