<script setup>
import TodoList from './TodoList.vue';
import TodoCreate from './TodoCreate.vue';

const todos = [
  { id: 1, name: 'Finish English Paper', complete: false },
  { id: 2, name: 'Read Chapter 4', complete: false },
  { id: 3, name: 'Finish Science Project', complete: false }
];
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
