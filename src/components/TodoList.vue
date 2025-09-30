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
    <div class="flex flex-col gap-3 pb-30" v-if="Object.keys(todos).length > 0">
        <TodoItems v-for="(todo, key) in todos" :key="todo.id" :id="key+1" :idTodo="todo.id" :name="todo.text" :done="todo.complited" @delete="emitDelete" @update:done="emitUpdate" />
    </div>
        <p v-else class="text-center text-lg text-gray-200">No tasks available</p>
</template>