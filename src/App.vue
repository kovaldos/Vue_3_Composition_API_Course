<script setup>
import TheHeader from '@/components/TheHeader.vue'
import TheNav from '@/components/TheNav.vue'
import TheTimeline from '@/pages/TheTimeline.vue'
import TheActivities from '@/pages/TheActivities.vue'
import TheProgress from '@/pages/TheProgress.vue'
import { PAGE_ACTIVITIES, PAGE_PROGRESS, PAGE_TIMELINE } from '@/constants.js'
import { ref } from 'vue'
import { generateTimelineItems, normalizePageHash } from '@/functions.js'

const currentPage = ref(normalizePageHash())
const timelineItems = generateTimelineItems()
const activities = ['Coding', 'Reading', 'Training']
function goTo(page) {
  currentPage.value = page
}
</script>

<template>
  <TheHeader @navigate="goTo($event)" />
  <main class="flex-grow">
    <TheTimeline v-show="currentPage === PAGE_TIMELINE" :timelineItems="timelineItems" />
    <TheActivities v-show="currentPage === PAGE_ACTIVITIES" :activities="activities" />
    <TheProgress v-show="currentPage === PAGE_PROGRESS" />
  </main>
  <TheNav :current-page="currentPage" @navigate="goTo($event)" />
</template>
