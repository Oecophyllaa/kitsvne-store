<template>
  <div class="home">
    <HeaderStore />
    <HeroStore />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderStore from "@/components/HeaderStore.vue";
import HeroStore from "@/components/HeroStore.vue";

export default {
  name: "HomeView",
  components: {
    HeaderStore,
    HeroStore,
  },
};
</script>
