<template>
  <div class="border-x" :class="twitterBorderColour">
    <div
      class="sticky top-0 px-4 py-3 bg-white/80 backdrop-blur-md dark:bg-dim-900/80"
    >
      <h1 class="text-xl font-bold text-gray-800 dark:text-gray-100">
        {{ props.title }}
      </h1>
    </div>
    <div
      v-if="props.loading"
      class="flex items-center justify-center p-4 border-b"
      :class="twitterBorderColour"
    >
      <LoaderSpinner />
    </div>
    <div v-else>
      <slot></slot>
    </div>
  </div>
</template>
<script setup>
const { twitterBorderColour, defaultTransition } = useTailwindConfig();
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  loading: {
    type: Boolean,
    required: true,
  },
});
</script>
