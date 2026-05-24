<script setup>
import { ref } from 'vue'
import { RouterLink, useRoute } from 'vue-router'
import { navLinks } from '../../data/eventData.js'

const route = useRoute()
const mobileOpen = ref(false)

function toggleMobile() {
  mobileOpen.value = !mobileOpen.value
}
function closeMobile() {
  mobileOpen.value = false
}
</script>

<template>
  <header class="bg-white border-b border-neutral-200 sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-6 sm:px-8">
      <div class="flex items-center justify-between h-14">

        <!-- Brand -->
        <RouterLink
          to="/"
          class="text-sm font-bold tracking-widest uppercase text-neutral-950 hover:text-neutral-600 transition-colors"
          @click="closeMobile"
        >
          Probably Paradoxical
        </RouterLink>

        <!-- Desktop nav -->
        <nav class="hidden md:flex items-center gap-7" aria-label="Primary navigation">
          <RouterLink
            v-for="link in navLinks"
            :key="link.to"
            :to="link.to"
            class="text-sm font-medium transition-colors"
            :class="route.path === link.to
              ? 'text-neutral-950 border-b-2 border-neutral-950 pb-0.5'
              : 'text-neutral-500 hover:text-neutral-950'"
          >
            {{ link.label }}
          </RouterLink>
        </nav>

        <!-- Login + hamburger -->
        <div class="flex items-center gap-3">
          <RouterLink
            to="/login"
            class="hidden sm:inline-flex items-center px-4 py-1.5 text-sm font-semibold bg-neutral-950 text-white rounded-sm hover:bg-neutral-800 transition-colors"
          >
            Team Login
          </RouterLink>

          <button
            class="md:hidden flex flex-col gap-1.5 p-1.5 text-neutral-700 hover:text-neutral-950"
            :aria-expanded="mobileOpen"
            aria-label="Toggle navigation"
            @click="toggleMobile"
          >
            <span class="block w-5 h-0.5 bg-current transition-all duration-200" :class="mobileOpen ? 'rotate-45 translate-y-2' : ''" />
            <span class="block w-5 h-0.5 bg-current transition-all duration-200" :class="mobileOpen ? 'opacity-0' : ''" />
            <span class="block w-5 h-0.5 bg-current transition-all duration-200" :class="mobileOpen ? '-rotate-45 -translate-y-2' : ''" />
          </button>
        </div>
      </div>

      <!-- Mobile nav -->
      <nav
        v-show="mobileOpen"
        class="md:hidden border-t border-neutral-100 py-3 flex flex-col gap-1"
        aria-label="Mobile navigation"
      >
        <RouterLink
          v-for="link in navLinks"
          :key="link.to"
          :to="link.to"
          class="px-2 py-2 text-sm font-medium transition-colors"
          :class="route.path === link.to
            ? 'text-neutral-950 bg-neutral-100'
            : 'text-neutral-500 hover:text-neutral-950 hover:bg-neutral-50'"
          @click="closeMobile"
        >
          {{ link.label }}
        </RouterLink>
        <RouterLink
          to="/login"
          class="mt-2 mx-2 px-4 py-2 text-sm font-semibold bg-neutral-950 text-white text-center hover:bg-neutral-800 transition-colors"
          @click="closeMobile"
        >
          Team Login
        </RouterLink>
      </nav>
    </div>
  </header>
</template>
