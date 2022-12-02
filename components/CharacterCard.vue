<script lang="ts" setup>
const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  image: {
    type: String,
    required: true,
  },
  status: {
    type: String,
    required: true,
  },
  id: {
    type: String,
    required: true,
  },
  species: {
    type: String,
    required: true,
  },
  location: {
    type: String,
    required: true,
  },
})

const grayScaleWhenDead = computed(() =>
  props.status === "Dead" ? { grayscale: true } : {}
)
</script>

<template>
  <NuxtLink :to="`/characters/${id}`">
    <div
      class="aspect-w-1 aspect-h-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-w-7 xl:aspect-h-8"
    >
      <NuxtImg
        :src="image"
        :alt="name"
        class="h-full w-full"
        :modifiers="grayScaleWhenDead"
      />
    </div>
    <h3 class="text-sm text-gray-700">{{ name }}</h3>
    <p class="mt-1 text-sm text-gray-500">Status: {{ status }}</p>
    <p class="mt-1 text-sm text-gray-500">Species: {{ species }}</p>
    <p class="mt-1 text-sm text-gray-500">Location: {{ location }}</p>
  </NuxtLink>
</template>
