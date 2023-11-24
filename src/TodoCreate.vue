<script setup></script>
<template>
  <form @submit.prevent="add">
    <div class="border border-gray-600 text-black mt-5">
      <input v-model="newTodo" placeholder="todo ..." class="p-1" />
      <input v-model="newTag" placeholder="tag ..." class="p-1 border-l" />
      <button type="submit" class="bg-white p-1 border-l">Add</button>
    </div>
  </form>
</template>
