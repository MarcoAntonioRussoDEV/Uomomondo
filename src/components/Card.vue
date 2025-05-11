<template>
  <div class="hero bg-base-200 rounded-lg p-10">
    <div
      class="hero-content flex-col"
      :class="{ 'lg:flex-row-reverse': reverse, 'lg:flex-row': !col }"
    >
      <img v-if="imgSrc" :src="imgSrc" class="max-w-sm rounded-lg shadow-2xl" />
      <div>
        <h2 class="text-5xl font-bold capitalize">{{ cardTitle }}</h2>
        <p class="py-6 textc">
          <slot />
        </p>
        <button class="btn btn-primary capitalize" v-if="buttonText">{{ buttonText }}</button>
      </div>
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
    imgSrc: {
      type: String,
      required: true,
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
