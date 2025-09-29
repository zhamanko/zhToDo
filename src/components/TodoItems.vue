<script setup>

const props = defineProps({
    id: {
        type: Number,
        required: true
    },
    idTodo: {
        type: Number,
        required: true
    },
    name: {
        type: String,
        required: true
    },
    done: {
        type: Boolean,
        required: true
    }
});

const emit = defineEmits(['update:done', 'delete']);

function toggleCheck() {
    emit('update:done', props.idTodo);
}

function deleteItem() {
    emit('delete', props.idTodo);
}

</script>

<template>
    <div class="todo-item">
        <input @click="toggleCheck" type="checkbox" :checked="props.done"  true-value="true" false-value="false" id="">
        <p>{{ props.id }}. <span>{{ props.name }}</span> <span>{{ props.done ? "done" : "not done" }}</span></p>
        <button @click="deleteItem">delete</button>
    </div>
</template>

<style>
.todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
}
</style>
