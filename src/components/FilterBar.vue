<script setup>
import { ref } from 'vue';

const emit = defineEmits(['filter-changed']);
let filter = ref('all');

function setFilter(value) {
    filter.value = value;
    emit('filter-changed', value);
}
</script>

<template>
    <div class="flex justify-around w-80">
        <button @click="setFilter('all')" :class="filter === 'all' ? 'text-blue-300' : '' ">All</button>
        <button @click="setFilter('active')" :class="filter === 'active' ? 'text-blue-300' : '' ">Active</button>
        <button @click="setFilter('finished')" :class="filter === 'finished' ? 'text-blue-300' : '' ">Finished</button>
    </div>
</template>