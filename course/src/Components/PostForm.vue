<template>
   <form @submit.prevent>
            <h4>Create a post</h4>
            <my-input v-model="post.title" placeholder="Title"/>
            <my-input v-model="post.body" placeholder="Description"/>
            <my-button @click="createPost" style="align-self: flex-end; margin-top: 15px">
                Create
            </my-button>
        </form>
</template>

<script>

export default {
    data() {
        return {
            post: {
                title: '',
                body: '', 
            }
        };
    },
    methods: {
        createPost() {
            this.post.id = Date.now;
            this.$emit('createPost', this.post);
            this.post = {
                title: '',
                body: ''
            };
        }
    }
}
</script>

<style scoped>

form {
    display: flex;
    flex-direction: column;
}   

</style>