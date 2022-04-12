<template>
    <div class="form-todo form-group">
        <p>
            <input placeholder="nome" type="text" v-model="name" name="author" class="form-control"/>
        </p>
        <p>
            <textarea placeholder="Comentário" v-model="message" name="message" class="form-control"></textarea>
        </p>
        <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
    </div>
</template>

<script>
export default{
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
        addComment() {
            if (this.message.trim() === '') {
                return;
            }

            this.$emit('add-todo', {
                name: this.name,
                message: this.message
            })

            this.name = ''
            this.message = ''
        },
    }
}
</script>