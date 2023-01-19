<template>
  <div class="product">
    <HeaderStore />
    <h1>Halaman Produk</h1>
    <FooterStore />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderStore from "@/components/HeaderStore.vue";
import FooterStore from "@/components/FooterStore.vue";

export default {
  name: "ProductView",
  components: {
    HeaderStore,
    FooterStore,
  },
};
</script>
