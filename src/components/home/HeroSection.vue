<script setup>
import StatCard from '../common/StatCard.vue'
import BaseButton from '../common/BaseButton.vue'
import { heroStats } from '../../data/eventData.js'
</script>

<template>
  <section class="relative py-14 md:py-20 overflow-hidden">

    <!-- Subtle dot grid -->
    <div class="absolute inset-0 -z-10 opacity-[0.05] pointer-events-none" aria-hidden="true">
      <svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <pattern id="hero-grid" width="32" height="32" patternUnits="userSpaceOnUse">
            <circle cx="1" cy="1" r="1" fill="black" />
          </pattern>
        </defs>
        <rect width="100%" height="100%" fill="url(#hero-grid)" />
      </svg>
    </div>

    <div class="max-w-7xl mx-auto px-6 sm:px-8 flex flex-col items-center text-center">

      <!-- Eyebrow -->
      <div class="inline-flex items-center gap-2 px-3 py-1 border border-neutral-300 mb-6">
        <span class="text-xs font-semibold uppercase tracking-widest text-neutral-500">
          Paradox'26 · IIT Madras
        </span>
      </div>

      <!-- Heading -->
      <h1 class="text-4xl sm:text-5xl md:text-6xl font-bold text-neutral-950 tracking-tight leading-tight max-w-3xl">
        Probably<br class="hidden sm:block" /> Paradoxical
      </h1>

      <!-- Subtitle -->
      <p class="mt-3 text-base text-neutral-500 font-medium max-w-xl">
        A team-based statistical paradox exploration event at Paradox'26, IIT Madras.
      </p>

      <!-- Description -->
      <p class="mt-3 text-sm text-neutral-400 max-w-xl leading-relaxed">
        Teams select a statistical paradox, design a survey, collect real campus data,
        run analysis, and present findings to a panel of judges — across five stages.
      </p>

      <!-- CTAs -->
      <div class="mt-7 flex flex-col sm:flex-row gap-3">
        <BaseButton variant="primary" to="/guidelines">View Guidelines</BaseButton>
        <BaseButton variant="outline" to="/login">Team Login</BaseButton>
      </div>

      <!-- Stats row -->
      <div class="mt-10 grid grid-cols-2 sm:grid-cols-4 gap-px bg-neutral-200 border border-neutral-200 w-full max-w-xl">
        <StatCard
          v-for="stat in heroStats"
          :key="stat.label"
          :value="stat.value"
          :label="stat.label"
        />
      </div>

    </div>
  </section>
</template>
