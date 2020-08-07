<template>
    <div class="container">
        <h2>Posts</h2>
        <hr />
        <div class="list-group">
            <p v-if="posts.length <= 0">Nenhum Post</p>
            <div class="list-group-item card" v-for="(post, index) in allPosts"  v-bind:key="post">
                <h2><strong>{{ post.title }}</strong></h2>
                <p>{{post.postMessage}}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removePost(index)">Excluir</a>
                </div>
            </div>
        </div>
        <hr />
        <NewPost v-on:add-post="addPost"></NewPost>
    </div>
</template>

<script>
import NewPost from './NewPost';
export default {
    components: {
        NewPost
    },
    data(){
        return{
            posts:[]
        }
    },
    methods: {
        addPost(post){
            this.posts.unshift(post);
        },
        removePost(index){
            this.posts.splice(index,1);
        }
    },
    computed: {
        allPosts(){
            return this.posts.map(post=>({
                ...post,
                title: post.title.trim() === '' ? 'sem titulo' : post.title
            }))
        }
    }
}
</script>