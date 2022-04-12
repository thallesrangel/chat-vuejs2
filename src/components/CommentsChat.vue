<template>
    <div class="container">
        <h1>Comentários</h1>
        <a href="https://youtu.be/cSa-SMVMGsE">Vídeo do projeto</a>
        <hr>
        <FormTodo v-on:add-todo="addComment"></FormTodo>
        <p v-if="comments.length <= 0">Sem comentários...</p>
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in allComments" :key="comment">
            <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
            <p>{{ comment.message }}</p>
            <div>
                <a href="#" v-on:click.prevent="removeComment(index)" title="Excluir">Excluir</a>
            </div>
            </div>
        </div>
    </div>
</template>


<script>
import FormTodo from './FormTodo'

export default {
    components: {
        FormTodo
    },
    data() {
        return {
            comments: []
        }
    },
    methods: {
        addComment(comments) {
            this.comments.push(comments);
        },
        removeComment(index) {
            this.comments.splice(index, 1)
        }
    },
    computed: {
        allComments() {
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    },
    watch: {
        comments(val) {
            console.log('val', val)
        }
    }
}
</script>