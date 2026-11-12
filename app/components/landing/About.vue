<script setup lang="ts">
import type { IndexCollectionItem } from '@nuxt/content'

defineProps<{
  page: IndexCollectionItem
}>()
</script>

<template>
  <UPageSection
    :title="page.about.title"
    :description="page.about.description"
    :ui="{
      container: 'w-full max-w-none p-0!',
      title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium',
      description: 'mt-3! max-w-none text-left text-sm sm:text-base lg:text-sm text-muted'
    }"
  />
</template>

<style scoped>

</style>
