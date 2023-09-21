<script setup lang="ts">
import { ref, computed } from 'vue';
import AssignmentItem from './AssignmentItem.vue';
import AssignmentTags from './AssignmentTags.vue';
import AssignmentPanels from './AssignmentPanels.vue';

const props = defineProps({
  assignments: Array,
  title: String,
  canToggle: { type: Boolean, default: false },
});

const currentTag = ref('all');

const filteredAssignments = computed(() => {
  if (currentTag.value === 'all') {
    return props.assignments;
  }
  return props.assignments?.filter((a) => a.tag === currentTag.value);
});
</script>

<template>
  <AssignmentPanels v-show="AssignmentItem.length" class="w-60">
    <div class="flex justify-between items-start">
      <h2 class="font-bold mb-2">
        {{ title }}
        <span>({{ AssignmentItem.length }})</span>
      </h2>

      <button v-show="canToggle" @click="$emit('toggle')">&times;</button>
    </div>

    <AssignmentTags 
      v-model:currentTag="currentTag" 
      :initial-tags="AssignmentItem.map(a => a.tag)"
    />

    <ul class="border border-gray-600 divide-y divide-gray-600 mt-6">
      <AssignmentItem 
        v-for="AssignmentItem in filteredAssignments"
        :assignment="AssignmentItem"
        :key="AssignmentItem.id"
      />
    </ul>

    <slot />
  </AssignmentPanels>
</template>