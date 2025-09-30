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
    <div class="flex gap-5">
        <input type="text" v-model='todoText' placeholder="Add a todo" class="border-y-2 border-white/50 rounded-2xl px-2 
        outline-none hover:border-y-3 focus:border-y-3 transition-all md:w-120"/>
        <button @click="submitTodo" class="border border-white/40 py-1 px-6 rounded-xl bg-white/10">Add</button>
    </div>
</template>