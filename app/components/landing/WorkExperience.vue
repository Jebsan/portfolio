<script setup lang="ts">
import type { IndexCollectionItem } from '@nuxt/content'

defineProps<{
  page: IndexCollectionItem
}>()
</script>

<template>
  <div class="flex flex-col gap-8">
    <UPageSection
      :title="page.experience.title"
      :ui="{
        container: 'p-0! gap-4 sm:gap-4',
        title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium',
        description: 'mt-2'
      }"
    >
      <template #description>
        <div class="flex flex-col gap-2">
          <Motion
            v-for="(experience, index) in page.experience.items"
            :key="index"
            :initial="{ opacity: 0, transform: 'translateY(20px)' }"
            :while-in-view="{ opacity: 1, transform: 'translateY(0)' }"
            :transition="{ delay: 0.4 + 0.2 * index }"
            :in-view-options="{ once: true }"
            class="text-muted grid grid-cols-[auto_minmax(1rem,1fr)_minmax(0,auto)] items-center gap-3"
          >
            <p class="text-sm">
              {{ experience.date }}
            </p>
            <USeparator />
            <ULink
              class="flex min-w-0 items-center gap-1"
              :to="experience.company.url"
              target="_blank"
            >
              <span class="text-sm">
                {{ experience.position }}
              </span>
              <div
                class="inline-flex min-w-0 items-center gap-1"
                :style="{ color: experience.company.color }"
              >
                <span class="font-medium">{{ experience.company.name }}</span>
                <UIcon :name="experience.company.logo" />
              </div>
            </ULink>
          </Motion>
        </div>
      </template>
    </UPageSection>

    <UPageSection
      :title="page.education.title"
      :ui="{
        container: 'p-0! gap-4 sm:gap-4',
        title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium',
        description: 'mt-2'
      }"
    >
      <template #description>
        <div class="flex flex-col gap-2">
          <Motion
            v-for="(education, index) in page.education.items"
            :key="index"
            :initial="{ opacity: 0, transform: 'translateY(20px)' }"
            :while-in-view="{ opacity: 1, transform: 'translateY(0)' }"
            :transition="{ delay: 0.4 + 0.2 * index }"
            :in-view-options="{ once: true }"
            class="text-muted grid grid-cols-[auto_minmax(1rem,1fr)_minmax(0,auto)] items-center gap-3"
          >
            <p class="text-sm">
              {{ education.date }}
            </p>
            <USeparator />
            <ULink
              class="flex min-w-0 items-center gap-1"
              :to="education.school.url"
              target="_blank"
            >
              <span class="text-sm">
                {{ education.degree }}
              </span>
              <div
                class="inline-flex min-w-0 items-center gap-1"
                :style="{ color: education.school.color }"
              >
                <span class="font-medium">{{ education.school.name }}</span>
                <img
                  v-if="education.school.logo.startsWith('/')"
                  :src="education.school.logo"
                  :alt="`${education.school.name} logo`"
                  class="size-35 object-contain"
                >
                <UIcon
                  v-else
                  :name="education.school.logo"
                />
              </div>
            </ULink>
          </Motion>
        </div>
      </template>
    </UPageSection>
  </div>
</template>

<style scoped>

</style>
