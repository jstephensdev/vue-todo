<script setup>
import { computed } from 'vue';
const props = defineProps(['initialTags', 'activeTag']);

const tags = computed(() => {
  return ['all', ...new Set(props.initialTags)];
});
</script>

<template>
  <div class="flex gap-2">
    <button
      @click="$emit('update:activeTag', tag)"
      v-for="tag in tags"
      :key="tag"
      class="border rounded px-1 py-px text-xs"
      :class="{ 'border-blue-500 text-blue-500': tag === props.activeTag }"
    >
      {{ tag }}
    </button>
  </div>
</template>
