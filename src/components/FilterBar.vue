<script setup>
import { ref } from 'vue';

const emit = defineEmits(['filter-changed']);
let filter = 'all';

function setFilter(value) {
    filter = value;
    emit('filter-changed', filter);
}
</script>

<template>
    <div>
        <button @click="setFilter('all')">Всі</button>
        <button @click="setFilter('active')">Активні</button>
        <button @click="setFilter('finished')">Завершені</button>
    </div>
</template>