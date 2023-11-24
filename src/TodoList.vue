<script setup>
import { computed } from 'vue';
import Todo from './Todo.vue';
import TodoTags from './TodoTags.vue';

const props = defineProps(['todos', 'title', 'toggle']);

const activeTag = 'all';
const show = true;
const todosFilteredByTag = computed(() => {
  if (activeTag === 'all') {
    return props.todos;
  }
  return props.todos.filter((todo) => todo.tag === activeTag);
});
</script>
<template>
  <section v-show="props.todos.length" class="bg-gray-700 p-4 border border-gray-600 rounder-lg">
    <div class="flex justify-between items-start">
      <h2 class="font-bold mb-2">
        {{ props.title }} <span>({{ props.todos.length }})</span>
      </h2>
      <button v-show="toggle && show" @click="show = !show">&times;</button>
      <button v-show="!show && props.todos.length" @click="show = !show">+</button>
    </div>

    <div v-show="show">
      <TodoTags v-model:activeTag="activeTag" :initialTags="props.todos.map((todo) => todo.tag)" />
      <ul class="mt-6">
        <Todo v-for="todo in todosFilteredByTag" :key="todo.id" :todo="todo" />
      </ul>
    </div>
    <slot></slot>
  </section>
</template>
