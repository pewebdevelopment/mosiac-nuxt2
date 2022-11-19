<template>
  <div v-if="currentRoute">
    <!-- <span v-html="currentRoute"> </span> -->

    <br />
    <!-- {{ currentRoute.fullPath }} -->
    <br />
    {{ JSON.stringify(currentRoute) }}
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted, watch } from "vue";
// import { useRouter } from "vue-router";

import SidebarLinkGroup from "./SidebarLinkGroup.vue";

export default {
  name: "Sidebar",
  props: ["sidebarOpen"],
  components: {
    SidebarLinkGroup,
  },

  data() {
    return {
      currentRoute: "",
    };
  },

  // created runs on serverside
  // created() {
  //   this.currentRoute = this.$route.path;
  //   console.log(this.currentRoute);
  // },

  // runs on the client side
  mounted() {
    this.currentRoute = this.$route;
    console.log(this.currentRoute);
    // console.log(this.$route);
  },

  //const router = useRouter(); // This is how we use the userouter in Vue 3 and Vue Router 4
  // const currentRoute = router.currentRoute.value;

  setup(props, { emit }) {
    const trigger = ref(null);
    const sidebar = ref(null);

    let storedSidebarExpanded = true;
    onMounted(() => {
      storedSidebarExpanded = localStorage.getItem("sidebar-expanded");
    });

    const sidebarExpanded = ref(
      storedSidebarExpanded === null ? false : storedSidebarExpanded === "true"
    );

    // close on click outside
    const clickHandler = ({ target }) => {
      if (!sidebar.value || !trigger.value) return;
      if (
        !props.sidebarOpen ||
        sidebar.value.contains(target) ||
        trigger.value.contains(target)
      )
        return;
      emit("close-sidebar");
    };

    // close if the esc key is pressed
    const keyHandler = ({ keyCode }) => {
      if (!props.sidebarOpen || keyCode !== 27) return;
      emit("close-sidebar");
    };

    onMounted(() => {
      document.addEventListener("click", clickHandler);
      document.addEventListener("keydown", keyHandler);
    });

    onUnmounted(() => {
      document.removeEventListener("click", clickHandler);
      document.removeEventListener("keydown", keyHandler);
    });

    // watch(sidebarExpanded, () => {
    //   localStorage.setItem("sidebar-expanded", sidebarExpanded.value);
    //   if (sidebarExpanded.value) {
    //     document.querySelector("body").classList.add("sidebar-expanded");
    //   } else {
    //     document.querySelector("body").classList.remove("sidebar-expanded");
    //   }
    // });

    return {
      trigger,
      sidebar,
      sidebarExpanded,
    };
  },
};
</script>

//  let storedSidebarExpanded;

//     if (typeof window !== "undefined") {
//       // Perform localStorage action
//       storedSidebarExpanded = localStorage.getItem("sidebar-expanded");
//     }
//     if (localStorage.getItem("sidebar-expanded")) {
//       storedSidebarExpanded = localStorage.getItem("sidebar-expanded");
//     }

//     let storedSidebarExpanded;