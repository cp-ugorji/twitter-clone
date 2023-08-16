<template>
  <div :class="{ dark: darkMode }">
    <div class="bg-white dark:bg-dim-900">
      <MainSectionLoadingPage v-if="isAuthLoading" />

      <!-- if authenticated -->
      <div v-else-if="user" class="min-h-full">
        <div
          class="grid grid-cols-12 mx-auto sm:px-6 lg:max-w-7xl lg:px-8 lg:gap-5"
        >
          <!-- left column -->
          <div class="hidden md:block xs-col-span-1 xl:col-span-2">
            <div class="sticky top-0">
              <SidebarLeftSection />
            </div>
          </div>

          <!-- main column -->
          <main class="col-span-12 bg-red-100 md:col-span-8 xl:col-span-6">
            <router-view />
          </main>

          <!-- right column -->
          <div class="hidden col-span-12 md:block xl:col-span-4 md:col-span-3">
            <div class="sticky top-0">
              <SidebarRightSection />
            </div>
          </div>
        </div>
      </div>

      <AuthPage v-else />

      <UiModal :isOpen="postTweetModal" @on-close="handleModalClose">
        <TweetForm
          :replyTo="replyTweet"
          showReply
          :user="user"
          @onSuccess="handleFormSuccess"
        />
      </UiModal>
    </div>
  </div>
</template>
<script setup>
const darkMode = ref(true);
const { useAuthUser, initAuth, useAuthLoading, logout } = useAuth();
const isAuthLoading = useAuthLoading();
const {
  closePostTweetModal,
  usePostTweetModal,
  openPostTweetModal,
  useReplyTweet,
} = useTweets();
const user = useAuthUser();

const postTweetModal = usePostTweetModal();
const emitter = useEmitter();
const replyTweet = useReplyTweet();

emitter.$on("replyTweet", (tweet) => {
  openPostTweetModal(tweet);
});

emitter.$on("toggleDarkMode", () => {
  darkMode.value = !darkMode.value;
});

onBeforeMount(() => {
  initAuth();
});

function handleFormSuccess(tweet) {
  closePostTweetModal();

  navigateTo({
    path: `/status/${tweet.id}`,
  });
}

function handleModalClose() {
  closePostTweetModal();
}

function handleOpenTweetModal() {
  openPostTweetModal(null);
}

function handleUserLogout() {
  logout();
}
</script>
