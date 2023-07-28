<template>
  <div :class="{ dark: darkMode }">
    <div class="bg-white dark:bg-dim-900">
      <div class="min-h-full">
        <div
          class="grid grid-cols-12 mx-auto sm:px-6 lg:max-w-7xl lg:px-8 lg:gap-5"
        >
          <!-- left column -->
          <div class="hidden md:block xs-col-span-1 xl:col-span-2">
            <div class="sticky top-0">
              <SidebarLeftSession />
            </div>
          </div>

          <!-- main column -->
          <main
            class="col-span-12 bg-red-500 md:col-span-8 xl:col-span-6"
          ></main>

          <!-- right column -->
          <div class="hidden bg-blue-500 md:block xl:col-span-4 md:col-span-3">
            <div class="sticky top-0">
              <SidebarRightSession />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const darkMode = ref(true);
</script>
