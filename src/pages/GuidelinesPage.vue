<script setup>
import PublicLayout from '../components/layout/PublicLayout.vue'
import SectionHeader from '../components/common/SectionHeader.vue'
import config from '../data/content.yml'

/**
 * Converts any Google Docs share/edit/view URL into a preview embed URL.
 * Accepted input formats:
 *   https://docs.google.com/document/d/DOC_ID/edit
 *   https://docs.google.com/document/d/DOC_ID/edit?usp=sharing
 *   https://docs.google.com/document/d/DOC_ID/view
 *   https://docs.google.com/document/d/DOC_ID/pub
 * Returns null if the URL is empty or not a recognised Google Docs URL.
 */
function toGoogleDocsEmbedUrl(url) {
  if (!url || !url.trim()) return null
  const match = url.match(/\/document\/d\/([a-zA-Z0-9_-]+)/)
  if (!match) return null
  return `https://docs.google.com/document/d/${match[1]}/preview`
}

const embedUrl = toGoogleDocsEmbedUrl(config.guidelines?.googleDocUrl)
</script>

<template>
  <PublicLayout>
    <section class="max-w-7xl mx-auto px-6 sm:px-8 py-10 md:py-14">

      <SectionHeader
        eyebrow="Rules & format"
        heading="Event Guidelines"
        :subheading="embedUrl
          ? 'Document embedded from Google Docs — always shows the latest version.'
          : 'Full guidelines will be published here before Stage 0.'"
      />

      <div class="mt-8">

        <!-- ── Google Doc embed ── -->
        <iframe
          v-if="embedUrl"
          :src="embedUrl"
          title="Event Guidelines"
          class="w-full border border-neutral-200"
          style="height: clamp(500px, 80vh, 1000px);"
          loading="lazy"
          allowfullscreen
        />

        <!-- ── Placeholder ── -->
        <div
          v-else
          class="border border-dashed border-neutral-300 bg-neutral-50 h-64 flex flex-col items-center justify-center gap-2 text-center px-6"
        >
          <p class="text-sm text-neutral-400">Guidelines document not yet published.</p>
          <p class="text-xs text-neutral-300">
            Paste your Google Doc link into
            <code class="font-mono bg-white border border-neutral-200 px-1 py-0.5 text-neutral-500">
              guidelines.googleDocUrl
            </code>
            in <code class="font-mono bg-white border border-neutral-200 px-1 py-0.5 text-neutral-500">content.yml</code>
            and it will embed automatically.
          </p>
        </div>

      </div>
    </section>
  </PublicLayout>
</template>
