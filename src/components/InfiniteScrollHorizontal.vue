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
              <li v-for="(logo, index) in logos" :key="index">
                <a :href="logo.url" target="_blank" class="flex items-center h-24 w-40">
                  <img
                    :src="`/images/${logo.src}`"
                    :alt="`Logo ${logo.name}`"
                    class="h-full w-full object-contain fill-white [&>svg]:fill-white"
                  />
                </a>
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
  {
    name: 'Ambasciata di Pace',
    src: 'ambasciata_di_pace.svg',
    url: 'https://www.perugiassisi.org/',
  },
  {
    name: 'CSV Foggia',
    src: 'csv.svg',
    url: 'https://www.csvfoggia.it/',
  },
  {
    name: 'Millumino di Meno',
    src: 'millumino_di_meno.svg',
    url: 'https://www.rai.it/milluminodimeno/',
  },
  {
    name: 'Ottavia',
    src: 'ottavia.svg',
    url: 'https://www.facebook.com/ottaviafoggia/',
  },
  {
    name: 'Libera',
    src: 'libera.svg',
    url: 'https://www.libera.it/',
  },
  {
    name: 'Trash Challenge Foggia',
    src: 'trash_challenge_foggia.svg',
    url: 'https://www.facebook.com/trashchallengefoggia/',
  },
  {
    name: 'Scuole per la Pace',
    src: 'scuole_per_la_pace.svg',
    url: 'https://www.lamiascuolaperlapace.it/',
  },
  // '5.png',
  // '7.png',
  // '8.png',
  // '9.jpg',
  // '10.jpg',
  // '11.png',
  // '12.svg',
  // '13.png',
  // '14.svg',
  // '15.svg',
  // '16.svg',
  // '17.svg',
  // '18.png',
  // '19.png',
  // '20.png',
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
  methods: {
    getLogoPath(logoName) {
      // Per immagini nella cartella public
      return `${import.meta.env.BASE_URL}images/${logoName}`
    },
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
