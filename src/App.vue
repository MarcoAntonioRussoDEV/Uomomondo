<template>
  <Navbar />
  <div class="flex-1 container mx-auto">
    <RouterView v-slot="{ Component }">
      <Transition name="slide-fade" mode="out-in">
        <component :is="Component" />
      </Transition>
    </RouterView>
  </div>
  <Footer />
</template>

<script>
import { RouterView } from 'vue-router'
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

<style scoped>
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.2s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>
