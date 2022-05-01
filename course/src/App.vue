<template>
    <div class="app">
        <h1>Page with posts</h1>
        <my-button @click="showDialog" style="margin: 15px 0;">Create a post</my-button>
        <my-dialog v-model:show="dialogVisible">
            <post-form @createPost="onCreatePost"/>
        </my-dialog>
        <post-list :posts="posts" @remove="removePost"/>
    </div>
</template>

<script>
import PostForm from "@/Components/PostForm.vue"
import PostList from "@/Components/PostList.vue"

export default {
    components: {
        PostList, PostForm
    },
    data() {
        return {
            posts: [
                { id: 1, title: 'JavaScript', body: 'Description of the post'},
                { id: 2, title: 'JavaScript 2', body: 'Description of the post 2'},
                { id: 3, title: 'JavaScript 3', body: 'Description of the post 3'},
                { id: 4, title: 'JavaScript 4', body: 'Description of the post 4'},
            ],
            dialogVisible: false
        };
    },
    methods: {
        onCreatePost(post) {
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post) {
            this.posts = this.posts.filter(p => p.id !== post.id);
        },
        showDialog() {
            this.dialogVisible = true;
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 20px;
}



</style>