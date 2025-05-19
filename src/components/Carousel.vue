<template>
  <div class="carousel w-full max-h-48">
    <div
      v-for="(image, index) of images"
      :id="`slide${index}`"
      class="carousel-item relative w-full"
      :key="index"
    >
      <img :src="image" class="w-full object-cover" />
      <div class="absolute left-5 right-5 top-1/2 flex -translate-y-1/2 transform justify-between">
        <a :href="`#slide${index - 1 >= 0 ? index - 1 : images.length - 1}`" class="btn btn-accent"
          >❮</a
        >
        <a :href="`#slide${index + 1 < images.length ? index + 1 : 0}`" class="btn btn-accent">❯</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  props: {
    images: {
      type: Array,
      default: () => [],
    },
    year: {
      type: String,
      required: false,
    },
  },

  data() {
    return {
      loading: false,
      error: null,
    }
  },
}
</script>

<style scoped></style>
