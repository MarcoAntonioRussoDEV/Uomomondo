<template>
  <Navbar />
  <div class="flex-1 container mx-auto p-4"><RouterView /></div>
  <Footer />
</template>

<script>
import { RouterLink, RouterView } from 'vue-router'
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
import AOS from 'aos'
import 'aos/dist/aos.css'
AOS.init()

export default {
  name: 'App',
  components: {
    Navbar,
    Footer,
  },
}
</script>

<style scoped></style>
