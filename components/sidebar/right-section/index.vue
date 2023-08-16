<script setup>
import { SearchIcon } from "@heroicons/vue/24/outline";
const search = ref("");
const emitter = useEmitter();

function handleSearch() {
  useRouter().push({
    path: "/search",
    query: {
      q: search.value,
    },
  });
}

function handleToggleDarkMode() {
  emitter.$emit("toggleDarkMode");
}

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

const whoTFollowItems = ref([
  {
    image: "https://picsum.photos/200/200",
    name: "Peter Obi",
    handle: "@PeterObi",
    altenativeName: "Peter Obi",
  },
  {
    image: "https://picsum.photos/200/200",
    name: "Peter Obi",
    handle: "@PeterObi",
    altenativeName: "Peter Obi",
  },
  {
    image: "https://picsum.photos/200/200",
    name: "Peter Obi",
    handle: "@PeterObi",
    altenativeName: "Peter Obi",
  },
]);
</script>
<template>
  <div class="flex flex-col">
    <!-- Search bar -->
    <div class="relative m-2">
      <div
        class="absolute flex items-center h-full pl-4 text-gray-600 cursor-pointer"
      >
        <div class="w-6 h-6">
          <SearchIcon @click="handleSearch" />
        </div>
      </div>
      <input
        v-model="search"
        class="flex items-center w-full pl-12 text-sm font-normal text-black bg-gray-200 border border-gray-200 rounded-full shadow dark:text-gray-100 dark:bg-dim-400 dark:border-dim-400 focus:bg-gray-100 dark:focus:bg-dim-900 focus:outline-none focus:border focus:border-blue-200 h-9"
        placeholder="Search tweet"
        type="text"
      />
    </div>

    <!-- what's happening section -->
    <SidebarRightSectionPreviewCard title="What's happening">
      <SidebarRightSectionPreviewCardItem
        v-for="whatsHappeningItem in whatsHappeningItems"
      >
        <div>
          <h2 class="font-bold text-gray-800 text-md dark:text-white">
            {{ whatsHappeningItem.title }}
          </h2>
          <p class="text-xs text-gray-400">{{ whatsHappeningItem.count }}</p>
        </div>
      </SidebarRightSectionPreviewCardItem>
    </SidebarRightSectionPreviewCard>
    <!-- who to follow ction -->
    <SidebarRightSectionPreviewCard title="Who to follow">
      <SidebarRightSectionPreviewCardItem v-for="whoTFollow in whoTFollowItems">
        <div class="flex flex-row items-center justify-between p-2">
          <div class="flex flex-row">
            <!-- image -->
            <img
              class="w-10 h-10 rounded-full"
              :src="whoTFollow.image"
              :alt="whoTFollow.altenativeName"
            />

            <!-- name and handle -->
            <div class="flex flex-col ml-2">
              <h1 class="text-sm font-bold text-gray-900 dark:text-white">
                {{ whoTFollow.name }}
              </h1>
              <p class="text-xs text-gray-400">{{ whoTFollow.handle }}</p>
            </div>
          </div>
          <!-- button section -->
          <div class="flex h-full">
            <button
              class="px-4 py-2 font-bold text-xs text-white dark:text-black bg-black dark:bg-white rounded-full"
            >
              Follow
            </button>
          </div>
        </div>
      </SidebarRightSectionPreviewCardItem>
    </SidebarRightSectionPreviewCard>

    <footer>
      <ul class="mx-2 my-4 text-xs text-gray-500">
        <li class="inline-block mx-2">
          <a
            href="#"
            class="hover:underline"
            @click.prevent="handleToggleDarkMode"
            >Dark mode</a
          >
        </li>
        <li class="inline-block mx-2">
          <a href="#" class="hover:underline">Privacy Policy</a>
        </li>
        <li class="inline-block mx-2">
          <a href="#" class="hover:underline">Cookie Policy</a>
        </li>
        <li class="inline-block mx-2">
          <a href="#" class="hover:underline">Accessability</a>
        </li>
        <li class="inline-block mx-2">
          <a href="#" class="hover:underline">Ads info</a>
        </li>
        <li class="inline-block mx-2">
          <a href="#" class="hover:underline">More</a>
        </li>
        <li class="inline-block mx-2">© 2022 Twitter, Inc.</li>
      </ul>
    </footer>
  </div>
</template>
