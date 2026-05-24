<script setup>
import PublicLayout from '../components/layout/PublicLayout.vue'
import SectionHeader from '../components/common/SectionHeader.vue'
</script>

<template>
  <PublicLayout>
    <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 md:py-14">
      <SectionHeader
        eyebrow="Participants"
        heading="Registered Teams"
        subheading="Team details will be listed here once registrations are confirmed."
      />
      <div class="mt-8 border border-dashed border-neutral-300 bg-neutral-50 min-h-48 flex items-center justify-center py-10">
        <p class="text-sm text-neutral-400">Team list coming soon.</p>
      </div>
    </section>
  </PublicLayout>
</template>
