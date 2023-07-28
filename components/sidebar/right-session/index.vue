<script setup>
const whatsHappeningItems = ref([
  {
    title: "SpaceX",
    count: "40.9k Tweets",
  },
  {
    title: "#JavaMeetsVue",
    count: "490.9m Tweets",
  },
  {
    title: "Renmoney",
    count: "98.9k Tweets",
  },
  {
    title: "Tennis",
    count: "406.9k Tweets",
  },
]);
</script>
<template>
  <div class="flex flex-col">
    <!-- what's happening session -->
    <SidebarRightSessionPreviewCard title="What's happening">
      <SidebarRightSessionPreviewCardItem
        v-for="whatsHappeningItem in whatsHappeningItems"
      >
        <div>
          <h2 class="font-bold text-gray-800 text-md dark:text-white">
            {{ whatsHappeningItem.title }}
          </h2>
          <p class="text-xs text-gray-400">{{ whatsHappeningItem.count }}</p>
        </div>
      </SidebarRightSessionPreviewCardItem>
    </SidebarRightSessionPreviewCard>
    <!-- who to follow session -->
    <SidebarRightSessionPreviewCard title="Who to follow" />
  </div>
</template>
