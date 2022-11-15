<template>
  <div class="flex h-screen overflow-hidden">
    <!-- Content area -->
    <div
      class="relative flex flex-col flex-1 overflow-y-auto overflow-x-hidden"
    >
      <!-- Site header -->
      <Header />

      <main>
        <div class="relative flex">
          <!-- Inbox sidebar -->
          <InboxSidebar
            :inboxSidebarOpen="inboxSidebarOpen"
            @close-inboxsidebar="inboxSidebarOpen = false"
          />

          <!-- Inbox body -->
          <InboxBody
            :inboxSidebarOpen="inboxSidebarOpen"
            @toggle-inboxsidebar="inboxSidebarOpen = !inboxSidebarOpen"
          />
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

import Header from "../partials/Header.vue";
import InboxSidebar from "../partials/inbox/InboxSidebar.vue";
import InboxBody from "../partials/inbox/InboxBody.vue";

export default {
  name: "Inbox",
  components: {
    Header,
    InboxSidebar,
    InboxBody,
  },
  setup() {
    const sidebarOpen = ref(false);
    const inboxSidebarOpen = ref(false);

    return {
      sidebarOpen,
      inboxSidebarOpen,
    };
  },
};
</script>