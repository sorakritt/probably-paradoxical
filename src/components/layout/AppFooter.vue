<script setup>
import { RouterLink } from 'vue-router'
import { eventMeta } from '../../data/eventData.js'
</script>

<template>
  <footer class="bg-white border-t border-neutral-200 mt-auto">
    <div class="max-w-7xl mx-auto px-6 sm:px-8 py-8">
      <div class="flex flex-col md:flex-row items-center justify-between gap-5">

        <!-- Brand -->
        <div class="text-center md:text-left">
          <p class="text-xs font-bold tracking-widest uppercase text-neutral-950">
            {{ eventMeta.name }}
          </p>
          <p class="text-xs text-neutral-400 mt-0.5">{{ eventMeta.edition }}</p>
        </div>

        <!-- Nav links -->
        <nav class="flex flex-wrap justify-center gap-5" aria-label="Footer navigation">
          <RouterLink to="/guidelines" class="text-xs text-neutral-500 hover:text-neutral-950 transition-colors">Guidelines</RouterLink>
          <RouterLink to="/timeline"   class="text-xs text-neutral-500 hover:text-neutral-950 transition-colors">Timeline</RouterLink>
          <RouterLink to="/teams"      class="text-xs text-neutral-500 hover:text-neutral-950 transition-colors">Teams</RouterLink>
          <RouterLink to="/judges"     class="text-xs text-neutral-500 hover:text-neutral-950 transition-colors">Judges</RouterLink>
        </nav>

        <!-- Copyright — sourced from content.yml → event.copyright -->
        <p class="text-xs text-neutral-400">
          © {{ new Date().getFullYear() }} {{ eventMeta.copyright }}
        </p>

      </div>
    </div>
  </footer>
</template>
