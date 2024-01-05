<script setup>
import { CheckCircleIcon } from '@heroicons/vue/24/solid/index.js'
import { PAGE_PROGRESS } from '@/constants.js'
</script>

<template>
  <a :href="`#${PAGE_PROGRESS}`" class="text-sm">
    <div v-if="false" class="flex items-center gap-1">
      <span class="whitespace-nowrap flex-shrink-0">Day complete!</span>
      <CheckCircleIcon class="flex-shrink-0 h-7 text-green-500" />
    </div>
    <div v-else class="flex items-center gap-1">
      <span class="whitespace-nowrap flex-shrink-0">
        Progress: <span class="font-mono">20%</span>
      </span>
      <span class="flex-shrink-0 h-3 w-3 rounded-full bg-red-500"></span>
    </div>
  </a>
</template>
