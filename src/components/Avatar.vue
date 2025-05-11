<template>
  <div class="avatar flex flex-col items-center gap-5">
    <div class="ring-primary ring-offset-base-100 w-24 rounded-full ring-2 ring-offset-2">
      <img :src="imgSrc" />
    </div>
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Avatar',
  props: {
    imgSrc: {
      type: String,
      required: true,
    },
  },
}
</script>

<style scoped></style>
