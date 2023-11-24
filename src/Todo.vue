<script setup>
defineProps(['todo']);
</script>
<template>
  <li>
    <label class="p-2">
      <input class="mr-2" type="checkbox" v-model="todo.complete" />{{ todo.name }}
    </label>
  </li>
</template>
