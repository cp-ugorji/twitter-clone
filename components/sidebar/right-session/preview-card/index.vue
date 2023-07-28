<template>
  <div
    class="m-2 border rounded-2xl bg-gray-50 dark:bg-dim-700 overflow-hidden"
    :class="twitterBorderColour"
  >
    <h1
      class="p-3 text-xl font-extrabold text-gray-900 border-b dark:text-white"
      :class="twitterBorderColour"
    >
      {{ props.title }}
    </h1>
    <!-- placeholder for item component -->
    <slot />
    <!--  -->
    <div
      class="p-3 text-sm text-blue-400 cursor-pointer hover:bg-gray-100 dark:hover:bg-dim-300"
      :class="defaultTransition"
    >
      show more
    </div>
  </div>
</template>
<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
});
const { twitterBorderColour, defaultTransition } = useTailwindConfig();
</script>
