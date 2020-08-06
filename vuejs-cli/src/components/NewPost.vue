<template>
    <div class="container">
        <h2>Novo Post</h2>
        <div class="form-group">
        <p>
            <input placeholder="Titulo" type="text" name="title" class="form-control" v-model="title"/> 
        </p>
        <p>
            <textarea placeholder="Escreva aqui o post" name="postMessage" class="form-control" v-model="postMessage"></textarea>
        </p>
        <button v-on:click.prevent="addPost" type="submit" class="btn btn-primary">Postar</button>
        </div>
    </div>
    
</template>

<script>
export default{
    data(){
        return{
            posts:[],
            title: '',
            postMessage: ''
        }
    },
    methods: {
        addPost(){
            console.log("chamado");
            if(this.postMessage.trim() === ''){
                return;
            }
            
            this.$emit('add-post', {
                title: this.title,
                postMessage: this.postMessage,
            });
            this.title = '';
            this.postMessage = '';
        }
    }
}
</script>

