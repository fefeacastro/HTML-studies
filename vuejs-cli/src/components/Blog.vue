<template>
    <div class="container">
        <h1> Blog</h1>
        <hr />
        <div class="list-group">
            <p v-if="posts.lenght <= 0">Sem comentários</p>
            <div class="list-group-item" v-for="(post,index) in allPosts"  v-bind:key="post">
                <span class="post_title"><strong>{{ post.title }}</strong></span>
                <p>{{post.postMessage}}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removePost(index)">Excluir</a>
                </div>
            </div>
        </div>
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
            this.posts.push(post);
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