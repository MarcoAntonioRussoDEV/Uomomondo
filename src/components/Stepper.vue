<template>
  <ul class="steps steps-vertical">
    <li v-for="(step, index) in steps" :key="index" class="text-nowrap step step-accent">
      {{ step.year }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Stepper',
  props: {
    steps: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style scoped></style>
