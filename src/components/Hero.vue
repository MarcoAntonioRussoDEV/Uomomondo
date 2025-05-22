<template>
  <header
    class="rounded-4xl p-6 sm:p-8 md:p-10 lg:px-32 bg-primary flex flex-col md:flex-row justify-center items-center gap-5 md:gap-10"
  >
    <div class="flex flex-col gap-5 md:gap-10 text-center md:text-left">
      <h1 class="text-5xl sm:text-6xl md:text-7xl lg:text-9xl font-bold">Uomo Mondo</h1>
      <div>
        <p class="text-lg sm:text-xl md:text-2xl">
          Siamo docenti e studenti con la voglia di condividere e sensibilizzare noi stessi, i
          nostri amici, la nostra città sui temi relativi alla pace
        </p>
      </div>
      <a href="#home" class="btn btn-accent btn-xl rounded-full w-fit mx-auto md:mx-0"
        >Esplora <Icon icon="line-md:arrow-down"
      /></a>
    </div>
    <img
      :src="headerImage"
      alt="header-image"
      class="mt-6 md:mt-0 max-w-full md:max-w-[50%] max-h-[50vh] md:max-h-[calc(100vh-20vh)]"
    />
  </header>
</template>

<script>
import { Icon } from '@iconify/vue'
import headerImage from '@/assets/images/uomomondo.png'

export default {
  name: 'Hero',
  data: () => ({
    headerImage,
  }),
  components: {
    Icon,
  },
}
</script>

<style scoped></style>
