<template>
  <div>
    <Sidebar
      :sidebarOpen="sidebarOpen"
      @close-sidebar="sidebarOpen.value = false"
    />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { ref } from "vue";
import Sidebar from "../partials/Sidebar.vue";
import Header from "../partials/Header.vue";

export default Vue.extend({
  name: "IndexPage",
  components: {
    Sidebar,
    Header,
  },
  setup() {
    const sidebarOpen = ref(false);

    return {
      sidebarOpen,
    };
  },
});
</script>



