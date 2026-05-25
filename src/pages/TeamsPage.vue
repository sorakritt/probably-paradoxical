<script setup>
import PublicLayout from '../components/layout/PublicLayout.vue'
import SectionHeader from '../components/common/SectionHeader.vue'
import BaseCard from '../components/common/BaseCard.vue'
import config from '../data/content.yml'
import teamInfo from '../data/teamInfo.yml'

const teamsContent = config.teams
</script>

<template>
  <PublicLayout>
    <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 md:py-14">
      <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3">
        <SectionHeader
          :eyebrow="teamsContent.eyebrow"
          :heading="teamsContent.heading"
          :subheading="teamsContent.subheading"
        />
        <p class="text-xs text-neutral-400 shrink-0">
          {{ teamsContent.lastUpdatedLabel }}
          <time :datetime="teamInfo.lastUpdatedIso">{{ teamInfo.lastUpdated }}</time>
        </p>
      </div>

      <div
        v-if="teamInfo.teams.length"
        class="mt-8 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4"
      >
        <BaseCard
          v-for="(team, index) in teamInfo.teams"
          :key="`${team.teamId}-${index}`"
          class="relative"
          :class="team.members.length >= 2 ? '!border-green-600' : '!border-red-600'"
        >
          <div
            class="absolute top-4 right-4 flex flex-col items-center gap-1"
            aria-label="Team ID"
          >
            <span class="w-12 h-12 border border-neutral-950 flex items-center justify-center p-1 text-center text-[11px] font-bold uppercase tracking-wide text-neutral-950 break-all">
              {{ team.teamId }}
            </span>
            <span class="text-[10px] uppercase tracking-wider text-neutral-400">Team ID</span>
          </div>
          <h3 class="pr-16 text-base font-bold text-neutral-950">{{ team.teamName }}</h3>
          <ul class="mt-4 space-y-3">
            <li
              v-for="(member, memberIndex) in team.members"
              :key="member.email"
            >
              <div class="flex flex-wrap items-center gap-2">
                <p class="text-sm font-medium text-neutral-950">{{ member.name }}</p>
                <span
                  v-if="memberIndex === 0"
                  class="inline-flex items-center px-2 py-0.5 text-[10px] font-semibold uppercase tracking-wider bg-violet-600 text-white"
                >
                  Lead
                </span>
              </div>
              <a
                :href="`mailto:${member.email}`"
                class="text-sm text-violet-700 hover:underline underline-offset-2 break-all"
              >
                {{ member.email }}
              </a>
            </li>
          </ul>
        </BaseCard>
      </div>

      <div
        v-else
        class="mt-8 border border-dashed border-neutral-300 bg-neutral-50 min-h-48 flex items-center justify-center py-10"
      >
        <p class="text-sm text-neutral-400">{{ teamsContent.emptyMessage }}</p>
      </div>
    </section>
  </PublicLayout>
</template>
