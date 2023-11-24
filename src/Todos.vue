<script setup>
import { reactive, computed } from 'vue';
import TodoList from './TodoList.vue';
import TodoCreate from './TodoCreate.vue';

const todos = reactive([
  { id: 1, name: 'Finish English Paper', complete: false, tag: 'English' },
  { id: 2, name: 'Read Chapter 4', complete: true, tag: 'Math' },
  { id: 3, name: 'Finish Science Project', complete: false, tag: 'Science' },
  { id: 4, name: 'Code Challenge', complete: true, tag: 'Programming' },
  { id: 5, name: 'Review Lab notes', complete: false, tag: 'Science' }
]);

const add = (newTodo) => {
  console.log(newTodo);
  todos.push({
    id: newTodo.length + 1,
    name: newTodo.name,
    complete: false,
    tag: newTodo.tag
  });
};

const inProcess = computed(() => {
  return todos.filter((todo) => !todo.complete);
});

const complete = computed(() => {
  return todos.filter((todo) => todo.complete);
});
</script>
<template>
  <section class="space-y-6">
    <section class="flex gap-4">
      <TodoList :todos="inProcess" title="In Progress">
        <TodoCreate @add="add" />
      </TodoList>
      <TodoList :todos="complete" title="Complete" toggle />
    </section>
  </section>
</template>
