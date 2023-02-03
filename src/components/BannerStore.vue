<template>
  <!-- Women Banner Section Begin -->
  <section class="women-banner spad">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12 mt-5" v-if="products.length > 0">
          <carousel class="product-slider" :items="3" :dots="false" :nav="false" :autoplay="true">
            <div class="product-item" v-for="itemProduct in products" v-bind:key="itemProduct.id">
              <div class="pi-pic">
                <img v-bind:src="itemProduct.galleries[0].photo" alt="" />
                <ul>
                  <li class="w-icon active">
                    <router-link to="/cart">
                      <i @click="saveKeranjang(itemProduct.id, itemProduct.name, itemProduct.price, itemProduct.galleries[0].photo)" class="icon_bag_alt"></i>
                    </router-link>
                  </li>
                  <li class="quick-view">
                    <router-link v-bind:to="'/product/' + itemProduct.id">+ Quick View</router-link>
                  </li>
                </ul>
              </div>
              <div class="pi-text">
                <div class="catagory-name">{{ itemProduct.type }}</div>
                <router-link v-bind:to="'/product/' + itemProduct.id">
                  <h5>{{ itemProduct.name }}</h5>
                </router-link>
                <div class="product-price">
                  ${{ itemProduct.price }}
                  <span>$35.00</span>
                </div>
              </div>
            </div>
          </carousel>
        </div>
        <div class="col-lg-12" v-else>
          <p>Produk terbaru belum tersedia untuk saat ini.</p>
        </div>
      </div>
    </div>
  </section>
  <!-- Women Banner Section End -->
</template>

<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "BannerStore",
  components: {
    carousel,
  },
  data() {
    return {
      products: [],
      keranjangUser: [],
    };
  },
  methods: {
    saveKeranjang(id, name, price, img) {
      var productStored = {
        id: id,
        name: name,
        price: price,
        photo: img,
      };

      this.keranjangUser.push(productStored);
      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);
    },
  },
  mounted() {
    if (localStorage.getItem("keranjangUser")) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
      } catch (e) {
        localStorage.removeItem("keranjangUser");
      }
    }
    axios
      .get("http://127.0.0.1:8000/api/products")
      .then((res) => (this.products = res.data.data.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.product-item {
  margin-right: 25px;
}
</style>
