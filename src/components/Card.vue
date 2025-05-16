<template>
  <div
    class="rounded-4xl p-10 transition-all duration-300"
    :class="{ 'bg-base-200!': isCollapsed }"
  >
    <div
      class="flex flex-col isolate gap-4 p-4 relative"
      :class="{ 'lg:flex-row-reverse': reverse, 'lg:flex-row': !col }"
    >
      <picture class="rounded-3xl shadow-2xl overflow-hidden"
        ><img v-if="imgSrc" :src="imgSrc" class="object-contain w-full"
      /></picture>
      <div>
        <h2 class="text-5xl font-bold capitalize">{{ cardTitle }}</h2>
        <p class="py-6 text-lg">
          <slot />
        </p>
        <button class="btn btn-primary capitalize" v-if="buttonText">{{ buttonText }}</button>
      </div>
    </div>
    <div class="collapse">
      <input type="checkbox" class="peer" v-model="isCollapsed" />
      <span class="collapse-title w-fit btn btn-link">
        {{ isCollapsed ? 'Mostra di meno' : 'Mostra di più' }}
      </span>
      <div class="collapse-content" v-if="collapse">
        {{ collapseContent }}
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
    collapse: {
      type: Boolean,
      default: false,
    },

    collapseContent: {
      type: String,
    },
  },
  data: () => ({
    isCollapsed: false,
  }),
}
</script>

<style scoped></style>
