<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps ({
  initialTags: Array,
  currentTag: String
})

const tags = computed(() => {
  return ['all', ...new Set(this.initialTags)]
})
</script>

<template>
  <div class="flex gap-2">
    <button
        @click="$emit('update:currentTag', tag)"
        v-for="tag in tags"
        class="border rounded px-1 py-px text-xs"
        :class="{
          'border-blue-500 text-blue-500': tag === currentTag 
        }"
        :key="tag.id"
    >{{ tag }}</button> 
  </div>  
</template>