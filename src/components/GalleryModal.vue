<template>
  <div
    v-if="selectedImage"
    class="fixed inset-0 bg-black bg-opacity-90 flex flex-col items-center justify-between z-50 px-6 py-10"
    @click="closeModal"
  >
    <div class="relative max-w-5xl h-full flex items-center" @click.stop>
      <!-- Controlli carosello -->
      <div class="absolute left-0 top-1/2 -translate-y-1/2 z-10">
        <button
          class="bg-black bg-opacity-50 hover:bg-opacity-70 text-white rounded-full p-2 m-2 transition-all duration-300"
          @click.stop="prevImage"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-8 h-8"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5 8.25 12l7.5-7.5" />
          </svg>
        </button>
      </div>

      <div class="absolute right-0 top-1/2 -translate-y-1/2 z-10">
        <button
          class="bg-black bg-opacity-50 hover:bg-opacity-70 text-white rounded-full p-2 m-2 transition-all duration-300"
          @click.stop="nextImage"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-8 h-8"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="m8.25 4.5 7.5 7.5-7.5 7.5" />
          </svg>
        </button>
      </div>

      <!-- Immagine principale -->
      <img
        :src="selectedImage"
        :key="currentImageIndex"
        class="max-w-full max-h-[65vh] object-contain mx-auto"
      />

      <!-- Indicatore posizione -->
      <div
        class="absolute bottom-4 left-1/2 -translate-x-1/2 text-white bg-black bg-opacity-50 px-3 py-1 rounded-full"
      >
        {{ currentImageIndex + 1 }} / {{ images.length }}
      </div>
    </div>

    <!-- Lista scorrevole di miniature - Carosello (posizione fissa in basso) -->
    <div class="w-full mt-auto mb-4 p-2 relative" @click.stop>
      <!-- Controlli carosello per le miniature -->
      <button
        class="absolute left-2 top-1/2 -translate-y-1/2 z-10 bg-black bg-opacity-50 hover:bg-opacity-70 text-white rounded-full p-2 transition-all duration-300"
        @click.stop="prevThumbnailPage"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5 8.25 12l7.5-7.5" />
        </svg>
      </button>

      <div class="overflow-hidden px-14 max-w-3xl mx-auto">
        <div
          class="flex transition-transform duration-300 ease-in-out"
          :style="{ transform: `translateX(-${thumbnailPageIndex * 100}%)` }"
        >
          <div
            v-for="(page, pageIndex) in thumbnailPages"
            :key="'page-' + pageIndex"
            class="flex min-w-full justify-center flex-shrink-0"
          >
            <div
              v-for="(imageIndex, idx) in page"
              :key="'thumb-' + imageIndex"
              class="inline-block cursor-pointer transition-transform duration-200 relative w-1/3 px-2"
              :class="{
                'scale-105 z-10': imageIndex === currentImageIndex,
                'opacity-40 hover:opacity-100': imageIndex !== currentImageIndex,
              }"
              @click.stop="selectImage(imageIndex)"
              :data-index="imageIndex"
            >
              <div
                class="aspect-ratio-box aspect-w-4 aspect-h-3 overflow-hidden rounded-lg shadow-md hover:shadow-xl"
              >
                <img
                  :src="images[imageIndex]"
                  :alt="`Miniatura ${imageIndex + 1}`"
                  class="w-full h-full object-cover"
                />
              </div>
              <div
                v-if="imageIndex === currentImageIndex"
                class="absolute -bottom-1 left-0 right-0 h-1 bg-primary"
              ></div>
            </div>
          </div>
        </div>
      </div>

      <button
        class="absolute right-2 top-1/2 -translate-y-1/2 z-10 bg-black bg-opacity-50 hover:bg-opacity-70 text-white rounded-full p-2 transition-all duration-300"
        @click.stop="nextThumbnailPage"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path stroke-linecap="round" stroke-linejoin="round" d="m8.25 4.5 7.5 7.5-7.5 7.5" />
        </svg>
      </button>

      <!-- Indicatori di pagina -->
      <div class="flex justify-center mt-2 space-x-2">
        <div
          v-for="(_, index) in thumbnailPages"
          :key="index"
          class="w-2 h-2 rounded-full transition-all duration-200"
          :class="
            index === thumbnailPageIndex ? 'bg-primary' : 'bg-gray-400 opacity-40 hover:opacity-60'
          "
          @click.stop="goToThumbnailPage(index)"
        ></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GalleryModal',
  props: {
    images: {
      type: Array,
      required: true,
    },
    initialImage: {
      type: String,
      default: null,
    },
  },

  data() {
    return {
      selectedImage: this.initialImage,
      currentImageIndex: -1,
      thumbnailPageIndex: 0,
      thumbnailsPerPage: 3,
    }
  },

  computed: {
    thumbnailPages() {
      // Dividi le miniature in pagine di 3 elementi ciascuna
      const pages = []
      const totalImages = this.images.length

      for (let i = 0; i < totalImages; i += this.thumbnailsPerPage) {
        // Creiamo un array di indici per ogni pagina
        const page = []
        for (let j = i; j < i + this.thumbnailsPerPage && j < totalImages; j++) {
          page.push(j)
        }
        pages.push(page)
      }

      return pages
    },

    currentPage() {
      // Trova la pagina che contiene l'immagine corrente
      if (this.currentImageIndex < 0) return 0

      return Math.floor(this.currentImageIndex / this.thumbnailsPerPage)
    },
  },

  watch: {
    initialImage: {
      immediate: true,
      handler(newValue) {
        if (newValue) {
          this.selectedImage = newValue
          this.currentImageIndex = this.images.indexOf(newValue)
          this.thumbnailPageIndex = this.currentPage
        }
      },
    },
  },

  created() {
    // Aggiungiamo i gestori per i tasti freccia
    window.addEventListener('keydown', this.handleKeyDown)
  },

  beforeUnmount() {
    // Rimuoviamo i gestori degli eventi quando il componente viene distrutto
    window.removeEventListener('keydown', this.handleKeyDown)
  },

  methods: {
    nextImage() {
      if (this.currentImageIndex < this.images.length - 1) {
        this.currentImageIndex++
      } else {
        // Torna all'inizio quando si raggiunge l'ultima immagine
        this.currentImageIndex = 0
      }
      this.selectedImage = this.images[this.currentImageIndex]
      // Aggiorna la pagina corrente del carosello
      this.thumbnailPageIndex = this.currentPage
    },

    prevImage() {
      if (this.currentImageIndex > 0) {
        this.currentImageIndex--
      } else {
        // Vai all'ultima immagine quando si è all'inizio
        this.currentImageIndex = this.images.length - 1
      }
      this.selectedImage = this.images[this.currentImageIndex]
      // Aggiorna la pagina corrente del carosello
      this.thumbnailPageIndex = this.currentPage
    },

    selectImage(index) {
      this.currentImageIndex = index
      this.selectedImage = this.images[index]
      // Aggiorna la pagina corrente del carosello
      this.thumbnailPageIndex = this.currentPage
    },

    closeModal() {
      this.selectedImage = null
      this.currentImageIndex = -1
      this.thumbnailPageIndex = 0
      this.$emit('close')
    },

    handleKeyDown(event) {
      // Verifichiamo che la modale sia aperta
      if (this.selectedImage) {
        switch (event.key) {
          case 'ArrowLeft':
            this.prevImage()
            break
          case 'ArrowRight':
            this.nextImage()
            break
          case 'Escape':
            this.closeModal()
            break
        }
      }
    },

    prevThumbnailPage() {
      if (this.thumbnailPageIndex > 0) {
        this.thumbnailPageIndex--
      } else {
        // Vai all'ultima pagina
        this.thumbnailPageIndex = this.thumbnailPages.length - 1
      }
    },

    nextThumbnailPage() {
      if (this.thumbnailPageIndex < this.thumbnailPages.length - 1) {
        this.thumbnailPageIndex++
      } else {
        // Torna alla prima pagina
        this.thumbnailPageIndex = 0
      }
    },

    goToThumbnailPage(pageIndex) {
      this.thumbnailPageIndex = pageIndex
    },
  },
}
</script>

<style scoped>
/* Stili per il carosello delle miniature */
.overflow-hidden {
  overflow: hidden;
}

/* Aspect ratio per le miniature */
.aspect-ratio-box {
  position: relative;
}

.aspect-ratio-box::before {
  content: '';
  display: block;
  padding-top: 75%; /* aspect ratio 4:3 */
}

.aspect-ratio-box img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Transizioni fluide per hover e focus */
img {
  transition: transform 0.2s ease;
}
</style>
