<script setup>
import TodoItems from './TodoItems.vue';

const props = defineProps({
    todos: {
        type: Object,
        required: true
    }
});

const emit = defineEmits(['update:done', 'delete']);

function emitDelete(id) {
    emit('delete', id);
}

function emitUpdate(id) {
    emit('update:done', id);
}
</script>

<template>
    <div>
        <TodoItems v-for="(todo, key) in todos" :key="todo.id" :id="key+1" :idTodo="todo.id" :name="todo.text" :done="todo.complited" @delete="emitDelete" @update:done="emitUpdate" />
    </div>
</template>