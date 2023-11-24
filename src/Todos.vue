<script setup>
// import { reactive, computed } from 'vue';
import TodoList from './TodoList.vue';
import TodoCreate from './TodoCreate.vue';

const todos = [
  { id: 1, name: 'Finish English Paper', complete: false, tag: 'Math' },
  { id: 2, name: 'Read Chapter 4', complete: true, tag: 'Science' },
  { id: 3, name: 'Finish Science Project', complete: false, tag: 'Science' }
];

const add = (newAssignment) => {
  todos.push({
    id: todo.length + 1,
    name: todo.name,
    complete: false,
    tag: todo.tag
  });
};

// const inProcess = computed(() => {
//   return todos.filter((todo) => !todo.complete);
// });

// const complete = computed(() => {
//   return todos.filter((todo) => todo.complete);
// });
</script>
<template>
  <section class="space-y-6">
    <section class="flex gap-4">
      <TodoList :todos="todos.filter((todo) => !todo.complete)" title="In Progress">
        <TodoCreate @add="add" />
      </TodoList>
      <TodoList :todos="todos.filter((todo) => todo.complete)" title="Complete" toggle />
    </section>
  </section>
</template>
