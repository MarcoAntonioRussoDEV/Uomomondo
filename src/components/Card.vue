<template>
  <div
    class="rounded-4xl p-10 transition-all duration-300"
    :class="{ 'bg-base-200!': isCollapsed }"
  >
    <div
      class="flex flex-col gap-4 p-4 relative items-center"
      :class="{ 'lg:flex-row-reverse': reverse, 'lg:flex-row': !col }"
    >
      <picture class="rounded-3xl overflow-hidden min-w-1/3"
        ><img v-if="imgSrc" :src="imgSrc" class="object-contain w-full"
      /></picture>
      <div class="flex flex-col justify-between">
        <h2 class="text-5xl font-bold capitalize">{{ cardTitle }}</h2>
        <div class="py-6 text-lg flex flex-col gap-4">
          <slot />
        </div>
        <RouterLink
          :to="buttonAction"
          class="btn btn-accent capitalize w-fit rounded-full"
          v-if="buttonText"
        >
          {{ buttonText }}
        </RouterLink>
      </div>
    </div>
    <div class="collapse" v-if="collapse">
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
    buttonAction: {
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
