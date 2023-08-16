<template>
  <div
    class="p-3 cursor-pointer hover:bg-gray-100 dark:hover:bg-dim-300 border-b"
    :class="wrapperClasses"
  >
    <slot />
  </div>
</template>
<script setup>
const { twitterBorderColour, defaultTransition } = useTailwindConfig();
const wrapperClasses = computed(
  () => `${defaultTransition} ${twitterBorderColour}`
);
</script>
