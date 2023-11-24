<script setup>
import Todo from './Todo.vue';
// import TodoTags from './TodoTags.vue';

defineProps(['todos', 'title']);

</script>
<template>
  <section v-show="todos.length" class="bg-gray-700 p-4 border border-gray-600 rounder-lg">
    <div class="flex justify-between items-start">
      <h2 class="font-bold mb-2">
        {{ title }} <span>({{ todos.length }})</span>
      </h2>
    </div>
    <ul class="mt-6">
      <Todo v-for="todo in todos" :key="todo.id" :todo="todo" />
    </ul>
    <slot></slot>
  </section>
</template>
