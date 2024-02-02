<script setup>
import NavItem from '@/components/NavItem.vue'
import { NAV_ITEMS } from '@/constants.js'
import { isPageValid } from '@/validators.js'
defineProps({
  currentPage: {
    type: String,
    required: true,
    validator: isPageValid
  }
})

const emit = defineEmits({
  navigate: isPageValid
})
</script>

<template>
  <nav class="sticky bottom-0 z-50 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(icon, page) in NAV_ITEMS"
        @click="emit('navigate', page)"
        :key="page"
        :href="`#${page}`"
        :class="{ 'bg-gray-200 pointer-events-none': page === currentPage }"
      >
        <component :is="icon" class="h-6 w-6" />
        {{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
