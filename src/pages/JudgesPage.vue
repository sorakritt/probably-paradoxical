<script setup>
import PublicLayout from '../components/layout/PublicLayout.vue'
import SectionHeader from '../components/common/SectionHeader.vue'
import BaseCard from '../components/common/BaseCard.vue'
import config from '../data/content.yml'

const { judges } = config
</script>

<template>
  <PublicLayout>
    <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 md:py-14">
      <SectionHeader
        :eyebrow="judges.eyebrow"
        :heading="judges.heading"
        :subheading="judges.subheading"
      />

      <div
        v-if="judges.profiles.length"
        class="mt-8 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
      >
        <BaseCard
          v-for="judge in judges.profiles"
          :key="judge.name"
        >
          <div class="aspect-4/3 bg-neutral-50 border border-neutral-100 mb-4 flex items-center justify-center overflow-hidden">
            <img
              v-if="judge.imageUrl"
              :src="judge.imageUrl"
              :alt="`${judge.name} portrait`"
              class="w-full h-full object-cover"
              loading="lazy"
            >
            <p v-else class="text-xs uppercase tracking-widest text-neutral-300">
              {{ judges.imagePlaceholder }}
            </p>
          </div>
          <h3 class="text-base font-bold text-neutral-950">{{ judge.name }}</h3>
          <p v-if="judge.role" class="mt-1 text-sm font-medium text-violet-700">
            {{ judge.role }}
          </p>
          <p v-if="judge.bio" class="mt-3 text-sm text-neutral-500 leading-relaxed">
            {{ judge.bio }}
          </p>
        </BaseCard>
      </div>

      <div
        v-else
        class="mt-8 border border-dashed border-neutral-300 bg-neutral-50 min-h-48 flex items-center justify-center py-10"
      >
        <p class="text-sm text-neutral-400">{{ judges.emptyMessage }}</p>
      </div>
    </section>
  </PublicLayout>
</template>
