<template>
  <div class="hero rounded-4xl p-10">
    <div class="w-full">
      <h2 class="text-5xl font-bold capitalize text-center">{{ cardTitle }}</h2>
      <p class="py-6">
        <slot />
      </p>
      <button class="btn btn-accent capitalize w-full rounded-full" v-if="buttonText">
        {{ buttonText }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    cardTitle: {
      type: String,
      required: true,
    },
    buttonText: {
      type: String,
      required: false,
    },

    col: {
      type: Boolean,
      default: false,
    },
    reverse: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style scoped></style>
