<script setup>
// we just want the home icon to me solid hence the import from solid
import { HomeIcon } from "@heroicons/vue/24/solid";
// others will be imported from othline
import {
  HashtagIcon,
  BellIcon,
  InboxIcon,
  BookmarkIcon,
  DocumentTextIcon,
  UserIcon,
  EllipsisHorizontalCircleIcon,
  PencilIcon,
  ChevronDownIcon,
} from "@heroicons/vue/24/outline";
// slight animation which can be reusable but for now I am using it for the twitter logo
const { defaultTransition } = useTailwindConfig();
const emits = defineEmits(["onTweet", "onLogout"]);

const props = defineProps({
  user: {
    type: Object,
    required: true,
  },
});
</script>
<template>
  <div class="flex flex-col h-screen">
    <!-- twitter logo session -->
    <div
      class="p-2 my-2 hover:bg-blue-50 rounded-full w-min dark:hover:bg-white/20"
      :class="defaultTransition"
    >
      <nuxt-link to="/">
        <div class="w-8 h-8">
          <logo-twitter />
        </div>
      </nuxt-link>
    </div>

    <!-- menu session -->
    <div class="mt-2 space-y-3">
      <SidebarLeftSectionTab active>
        <template v-slot:icon>
          <!-- home icon -->
          <HomeIcon />
        </template>
        <template v-slot:name>
          <!-- home Label -->
          Home
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- explore icon -->
          <HashtagIcon />
        </template>
        <template v-slot:name>
          <!-- explore Label -->
          Explore
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- notification icon -->
          <BellIcon />
        </template>
        <template v-slot:name>
          <!-- notification Label -->
          Notifications
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- message icon -->
          <InboxIcon />
        </template>
        <template v-slot:name>
          <!-- message Label -->
          Messages
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- bookmark icon -->
          <BookmarkIcon />
        </template>
        <template v-slot:name>
          <!-- bookmark Label -->
          Bookmarks
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- list icon -->
          <DocumentTextIcon />
        </template>
        <template v-slot:name>
          <!-- list Label -->
          Lists
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- user icon -->
          <UserIcon />
        </template>
        <template v-slot:name>
          <!-- user Label -->
          Profile
        </template>
      </SidebarLeftSectionTab>

      <SidebarLeftSectionTab>
        <template v-slot:icon>
          <!-- more icon -->
          <EllipsisHorizontalCircleIcon />
        </template>
        <template v-slot:name>
          <!-- user Label -->
          More
        </template>
      </SidebarLeftSectionTab>

      <div class="hidden xl:block">
        <UIButton liquid size="lg" @on-click="emits('onTweet')">
          <span class="font-bold"> Tweet </span>
        </UIButton>
      </div>

      <div class="block xl:hidden">
        <UIButton @on-click="emits('onTweet')">
          <div class="w-6 h-6 font-bold">
            <PencilIcon />
          </div>
        </UIButton>
      </div>
    </div>

    <div
      class="flex flex-row items-center justify-center px-2 py-2 mx-auto mt-auto mb-5 rounded-full cursor-pointer w-14 xl:w-full hover:bg-gray-100 dark:hover:bg-dim-800"
      :class="defaultTransition"
      @click="emits('onLogout')"
    >
      <div class="flex flex-row">
        <img :src="props.user.profileImage" class="w-10 h-10 rounded-full" />
        <div class="flex-col hidden ml-2 xl:block">
          <h1 class="text-sm font-bold text-gray-800 dark:text-white">
            {{ user.name }}
          </h1>
          <p class="text-sm text-gray-400">
            {{ user.handle }}
          </p>
        </div>
      </div>

      <!-- ICON -->
      <div class="hidden ml-auto xl:block">
        <div class="w-6 h-6">
          <ChevronDownIcon />
        </div>
      </div>
    </div>
  </div>
</template>
