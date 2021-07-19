<template>
    <p :class="['todo-item', todoItems.isCompleted ? 'is-completed' : '']">
        <input type="checkbox" :checked=todoItems.isCompleted @change="taskCompleted">
        {{ todoItems.title }}
        <button class="del-btn ml-10" @click="deleteItem">Delete</button>
    </p>
</template>

<script>
export default {
    name: 'TodoItems',
    props: ['todoItems'],
    setup(props, context) {
        const taskCompleted = () => {
            context.emit('item-completed', props.todoItems.id)
        }

        const deleteItem = () => {
            context.emit('delete-item', props.todoItems.id)
        }
        
        return {
            taskCompleted,
            deleteItem
        }
    }
}
</script>

<style>

.todo-item {
    background-color: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}

.del-btn {
  background: #ff0000;
  color: #fff;
  border: none;
  cursor: pointer;
  float: right;
}

.is-completed {
    text-decoration: line-through;
}

.ml-10 {
    margin-left: 10px;
}
</style>