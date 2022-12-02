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
  <div class="flex m-3 bg-gray-300 rounded-xl">
    <NuxtLink :to="`/characters/${id}`">
      <NuxtImg
        :src="image"
        class="rounded-xl object-cover"
        :modifiers="grayScaleWhenDead"
      />
      <div class="m-3">
        <h2 class="text-xl mb-3">{{ name }}</h2>
        <p>Status: {{ status }}</p>
        <p>Species: {{ species }}</p>
        <p>Location: {{ location }}</p>
      </div>
    </NuxtLink>
  </div>
</template>
