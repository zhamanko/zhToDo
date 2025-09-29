<script setup>
import { ref } from 'vue';

const todoText = ref('');

const emit = defineEmits(['add']);

function submitTodo() {
    if (todoText.value.trim()) {
        emit('add', todoText.value);
        todoText.value = '';
    } else {
        alert('Please enter a todo');
    }
}

</script>

<template>
    <input type="text" v-model='todoText' placeholder="Add a todo" />
    <button @click="submitTodo">Add</button>
</template>