<template>
  <header
    class="rounded-lg bg-primary p-10 xl:p-64 text-primary-content flex flex-col justify-center items-start gap-10"
  >
    <h1 class="text-7xl">Uomo Mondo</h1>
    <div>
      <p class="text-2xl">
        Siamo docenti e studenti con la voglia di condividere e sensibilizzare noi stessi, i nostri
        amici, la nostra città sui temi relativi alla pace
      </p>
    </div>
    <a href="#home" class="btn btn-secondary text-black"
      >Esplora <Icon icon="line-md:arrow-down"
    /></a>
  </header>
</template>

<script>
import { Icon } from '@iconify/vue'

export default {
  name: 'Hero',
  components: {
    Icon,
  },
}
</script>

<style scoped></style>
