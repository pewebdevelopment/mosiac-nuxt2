<template>
  <div class="flex h-screen overflow-hidden">
    <NuxtLink to="/">Home Page</NuxtLink>
    <!-- Sidebar -->
    <Sidebar :sidebarOpen="sidebarOpen" @close-sidebar="sidebarOpen = false" />
  </div>
</template>

<script>
import { ref } from "vue";
import Sidebar from "../partials/SidebarNuxt.vue";
import Header from "../partials/Header.vue";
// import { useRouter } from "vue-router";

export default {
  name: "Inbox",
  components: {
    Sidebar,
    Header,
  },
};
</script>
// const currentRoute = useRouter().currentRoute.value;
// console.log(currentRoute);
