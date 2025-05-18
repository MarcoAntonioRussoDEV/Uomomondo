<template>
  <div class="container mx-auto px-4">
    <nav class="flex justify-between items-center py-10">
      <h2 class="text-4xl uppercase font-bold">uomomondo</h2>

      <!-- Menu mobile (visibile solo su schermi < md) -->
      <details class="dropdown dropdown-end md:hidden">
        <summary class="btn btn-link no-underline" role="button">Links</summary>
        <ul
          class="capitalize menu dropdown-content border border-base-200 rounded-box w-auto z-[1] p-2 shadow-xl bg-base-100"
        >
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/about">About</RouterLink></li>
          <li><RouterLink to="/gallery">Gallery</RouterLink></li>
        </ul>
      </details>

      <!-- Menu desktop (visibile solo su schermi >= md) -->
      <ul class="hidden md:flex gap-6 capitalize text-xl items-center">
        <li class="cursor-pointer transition-colors"><RouterLink to="/">Home</RouterLink></li>
        <li class="cursor-pointer transition-colors"><RouterLink to="/about">About</RouterLink></li>
        <li class="cursor-pointer transition-colors">
          <RouterLink to="/gallery">Gallery</RouterLink>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import { RouterLink } from 'vue-router'
</script>

<style scoped>
ul > li > a {
  transition: color 0.3s ease;
}
.router-link-exact-active {
  color: var(--color-accent);
}
</style>
