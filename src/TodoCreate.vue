<script setup>
import { ref } from 'vue';
const emit = defineEmits(['add']);
let newTodo = ref('');
let newTag = ref('');

const add = () => {
  emit('add', {
    name: newTodo.value,
    tag: newTag.value.charAt(0).toUpperCase() + newTag.value.slice(1)
  });
  newTodo.value = '';
  newTag.value = '';
};
</script>
<template>
  <form @submit.prevent="add">
    <div class="border border-gray-600 text-black mt-5">
      <input v-model="newTodo" placeholder="todo ..." class="p-1" />
      <input v-model="newTag" placeholder="tag ..." class="p-1 border-l" />
      <button @submit="add" class="bg-white p-1 border-l">Add</button>
    </div>
  </form>
</template>
