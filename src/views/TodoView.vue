<script setup lang="ts">
import AssignmentPanels from '@/components/AssignmentPanels.vue';


</script>

<template>
  <section class="flex gap-10">
    <AssignmentPanels />
    <div class="rounded-lg w-fit p-5 border-2 border-gray-600">
      <h2 class="text-2xl mb-5">Steps</h2>
      <ol class="text-red text-lg">
        <li class="flex w-[320px] justify-between items-center">1. Review Section 4: <a class="underline text-red" href="https://laracasts.com/series/learn-vue-3-step-by-step/episodes/10">It's All So Easy</a><input type="checkbox"></li>
        <li class="flex w-[320px] justify-between items-center">2. Create Assignments panel<input type="checkbox"></li>
        <li class="flex w-[320px] justify-between items-center">3. Create Assignments list<input type="checkbox"></li>
        <li class="flex w-[320px] justify-between items-center">4. Create Assignment component<input type="checkbox"></li>
        <li class="flex w-[320px] justify-between items-center">5. Create Assignments add feature<input type="checkbox"></li>
        <li class="flex w-[320px] justify-between items-center">6. Clean it up<input type="checkbox"></li>
      </ol>
    </div>
  </section>
</template>