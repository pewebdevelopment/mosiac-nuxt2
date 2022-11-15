<script setup>
// import '@/assets/css/main.css'

const loading = ref(true);
onMounted(() => {
  if (localStorage.getItem("sidebar-expanded") == "true") {
    document.querySelector("body").classList.add("sidebar-expanded");
  } else {
    document.querySelector("body").classList.remove("sidebar-expanded");
  }
});

useHead({
  titleTemplate: (titleChunk) => {
    const titleBase = "Mosiac Nuxt 2";
    return titleChunk ? `${titleChunk} - ${titleBase}` : titleBase;
  },
});
</script>


<template>
  <div>
    <Nuxt />
  </div>
</template>