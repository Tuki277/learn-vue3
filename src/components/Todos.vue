<template>
  <AddTodo @add-Todo="addTodo"/>
  <TodoItems v-for="todo in todos" :key="todo.id" :todoItems="todo" @item-completed="taskCompleted" @delete-item="deleteItem"/>
</template>

<script>

import TodoItems from './TodoItems.vue'
import AddTodo from './AddTodo.vue'
import { ref } from 'vue'

export default {
    name: 'Todos',
    setup () {
      const todos = ref ([
        {
          id: 1,
          title: "Viec 1",
          isCompleted: false
        },
        {
          id: 2,
          title: "Viec 2",
          isCompleted: false
        },
        {
          id: 3,
          title: "Viec 3",
          isCompleted: false
        }
      ])

      const taskCompleted = id => {
        todos.value = todos.value.map(todo => {
          if (todo.id === id) {
            todo.isCompleted = !todo.isCompleted
          }
          return todo
        })
      }
      
      const deleteItem = id => {
        todos.value = todos.value.filter(todo => todo.id !== id)
      }

      const addTodo = newItem => {
        todos.value.push(newItem)
      }

      return {
        todos,
        taskCompleted,
        deleteItem,
        addTodo
      }
    },
    components: {
      TodoItems,
      AddTodo
    }
}
</script>

<style>

</style>