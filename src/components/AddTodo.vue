<template>
  <form @submit="addItem">
        <input type="text" placeholder="Việc mới..." v-model="title" />
        <input type="submit" value="Thêm" class="add-btn" />
  </form>
</template>

<script>

export default {
    name: 'AddTodo',
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addItem (e) {
            e.preventDefault()
            const newItem = {
                id: Math.random(),
                title: this.title,
                completed: false
            }
            this.$emit('add-Todo', newItem)
            this.title = ''
        }
    }
}
</script>

<style scoped>
form {
  display: flex;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>