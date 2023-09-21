<script setup lang="ts">
import { ref, computed, onMounted } from 'vue';
import AssignmentList from "./AssignmentList.vue";
import AssignmentCreate from "./AssignmentCreate.vue";

const assignments = ref([]);
const showCompleted = ref(true);

const filters = computed(() => {
  const inProgress = assignments.value.filter((assignment) => !assignment.complete);
  const completed = assignments.value.filter((assignment) => assignment.complete);
  return {
    inProgress,
    completed,
  };
});

onMounted(() => {
  fetch('http://localhost:3001/assignments')
    .then((response) => response.json())
    .then((fetchedAssignments) => {
      assignments.value = fetchedAssignments;
    });
});

const add = (name) => {
  assignments.value.push({
    name: name,
    completed: false,
    id: this.assignments.length + 1
  });
};
</script>


<template>
  <section class="flex gap-8">
      <AssignmentList :assignments="filters.inProgress" title="In Progress">
          <AssignmentCreate @add="add"></AssignmentCreate> 
      </AssignmentList>
      
      <div v-show="showCompleted">
          <AssignmentList 
              :assignments="filters.completed" 
              title="Completed" 
              can-toggle
              @toggle="showCompleted = !showCompleted"
          ></AssignmentList>
      </div> 
        </section>
</template>