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
} from "@heroicons/vue/24/outline";
// slight animation which can be reusable but for now I am using it for the twitter logo
const { defaultTransition } = useTailwindConfig();
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
      <SidebarLeftSessionTab active>
        <template v-slot:icon>
          <!-- home icon -->
          <HomeIcon />
        </template>
        <template v-slot:name>
          <!-- home Label -->
          Home
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- explore icon -->
          <HashtagIcon />
        </template>
        <template v-slot:name>
          <!-- explore Label -->
          Explore
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- notification icon -->
          <BellIcon />
        </template>
        <template v-slot:name>
          <!-- notification Label -->
          Notifications
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- message icon -->
          <InboxIcon />
        </template>
        <template v-slot:name>
          <!-- message Label -->
          Messages
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- bookmark icon -->
          <BookmarkIcon />
        </template>
        <template v-slot:name>
          <!-- bookmark Label -->
          Bookmarks
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- list icon -->
          <DocumentTextIcon />
        </template>
        <template v-slot:name>
          <!-- list Label -->
          Lists
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- user icon -->
          <UserIcon />
        </template>
        <template v-slot:name>
          <!-- user Label -->
          Profile
        </template>
      </SidebarLeftSessionTab>

      <SidebarLeftSessionTab>
        <template v-slot:icon>
          <!-- more icon -->
          <EllipsisHorizontalCircleIcon />
        </template>
        <template v-slot:name>
          <!-- user Label -->
          More
        </template>
      </SidebarLeftSessionTab>
    </div>
  </div>
</template>
