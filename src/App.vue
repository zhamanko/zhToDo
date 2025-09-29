<script setup>
import { ref, watch, computed } from 'vue';
import AddTodo from './components/AddTodo.vue';
import TodoList from './components/TodoList.vue';
import FilterBar from './components/FilterBar.vue';

const todos = ref([]);
const filter = ref('all');

const todoListFilter = computed(() => {
  if (filter.value === 'all') {
    return todos.value;
  } else if (filter.value === 'active') {
    return todos.value.filter(todo => !todo.complited);
  } else if (filter.value === 'finished') {
    return todos.value.filter(todo => todo.complited);
  }
  return todos.value;
});

const savedTodos = localStorage.getItem('todos');
if (savedTodos) {
  todos.value = JSON.parse(savedTodos);
}

function addTodo(text) {
  if (text.trim()) {
    todos.value.push({
      id: Date.now(),
      text: text,
      complited: false
    })
  }
}

function toggleFilter(newFilter) {
  filter.value = newFilter;
}

function deleteTodo(id) {
  todos.value = todos.value.filter(todo => todo.id !== id);
}

function updateTodo(id) {
  const todo = todos.value.find(todo => todo.id === id);
  if (todo) {
    todo.complited = !todo.complited;
  }
}

watch(todos, (newTodos) => {
  localStorage.setItem('todos', JSON.stringify(newTodos));
}, { deep: true });

</script>

<template>
  <h1>zhToDo</h1>
  <div class="add-container">
    <AddTodo @add="addTodo" />
  </div>
  <div class="list-container">
    <TodoList :todos="todoListFilter" @delete="deleteTodo" @update:done="updateTodo" />
  </div>
  <div>
    <FilterBar @filter-changed="toggleFilter"/>
  </div>
</template>

<style scoped>
h1 {
  text-align: center;
  color: #272727;
}

.add-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
</style>
