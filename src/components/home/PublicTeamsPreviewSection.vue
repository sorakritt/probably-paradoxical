<script setup>
import SectionHeader from '../common/SectionHeader.vue'
import BaseButton from '../common/BaseButton.vue'

const placeholderCount = 6
</script>

<template>
  <section class="py-10 md:py-12 border-t border-neutral-200 bg-neutral-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

      <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 mb-8">
        <SectionHeader
          eyebrow="Participants"
          heading="Registered Teams"
          subheading="Team profiles will appear here once registrations are confirmed."
        />
        <BaseButton variant="outline" to="/teams" class="w-full sm:w-auto">
          View All Teams
        </BaseButton>
      </div>

      <!-- 2-col on all mobile, 3-col tablet, 6-col desktop -->
      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-3">
        <div
          v-for="n in placeholderCount"
          :key="n"
          class="border border-dashed border-neutral-300 bg-white h-16 sm:h-20 flex items-center justify-center"
          aria-hidden="true"
        >
          <span class="text-xs text-neutral-300 uppercase tracking-widest font-medium">TBA</span>
        </div>
      </div>

      <p class="mt-5 text-xs text-neutral-400 text-center">
        Team names will be announced after registration closes.
      </p>

    </div>
  </section>
</template>
