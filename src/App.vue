<script setup lang="ts">
import HomeView from "./views/HomeView.vue";
import Toast from "primevue/toast";
</script>

<template>
  <HomeView />
  <Toast />
</template>

<style>
@import "@/assets/base.css";
@import "/node_modules/primeflex/primeflex.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 0;
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    padding: 0 2rem;
  }

  header {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
