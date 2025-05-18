<template>
  <div class="relative font-inter antialiased">
    <main class="relative flex flex-col justify-center overflow-hidden">
      <div class="w-full mx-auto container px-4">
        <div class="text-center">
          <!-- Logo Carousel animation  -->
          <div
            class="w-full inline-flex flex-nowrap overflow-hidden [mask-image:_linear-gradient(to_right,transparent_0,_black_128px,_black_calc(100%-128px),transparent_100%)] animate-container"
          >
            <ul
              ref="logos"
              class="flex items-center justify-center md:justify-start [&_li]:mx-8 [&_img]:max-w-none animate-infinite-scroll"
            >
              <li v-for="(logo, index) in logos" :key="index" class="flex items-center h-24 w-40">
                <img
                  :src="`/images/${logo}`"
                  :alt="`Logo ${index + 1}`"
                  class="h-full w-full object-contain fill-white [&>svg]:fill-white"
                />
              </li>
            </ul>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
const logos = [
  'ambasciata_di_pace.svg',
  'csv.svg',
  'millumino_di_meno.svg',
  'ottavia.svg',
  '5.png',
  'trash_challenge_foggia.svg',
  '7.png',
  '8.png',
  '9.jpg',
  '10.jpg',
  '11.png',
  '12.svg',
  '13.png',
  '14.svg',
  '15.svg',
  '16.svg',
  '17.svg',
  '18.png',
  '19.png',
  '20.png',
]
export default {
  name: 'InfiniteScrollHorizontal',
  data() {
    return {
      bannerOpen: true,
      logos,
    }
  },
  mounted() {
    if (this.$refs.logos) {
      const clone = this.$refs.logos.cloneNode(true)
      clone.setAttribute('aria-hidden', 'true')
      this.$refs.logos.parentNode.appendChild(clone)
    }
  },
}
</script>

<style scoped>
.animate-infinite-scroll {
  animation: infiniteScroll 25s linear infinite;
}
.animate-container:hover .animate-infinite-scroll {
  animation-play-state: paused;
}

@keyframes infiniteScroll {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}
</style>
