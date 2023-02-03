<template>
  <div class="product">
    <HeaderStore />
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="breadcrumb-text product-more">
              <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
              <span>Detail</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="row">
              <div class="col-lg-6">
                <div class="product-pic-zoom">
                  <img class="product-big-img" :src="default_img" alt="" />
                </div>
                <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                  <carousel class="product-thumbs-track ps-slider" :dots="false" :nav="false">
                    <div v-for="img in productDetails.galleries" :key="img.id" class="pt" @click="changeImg(img.photo)" :class="img.photo == default_img ? 'active' : ''">
                      <img :src="img.photo" alt="" />
                    </div>
                  </carousel>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="product-details text-left">
                  <div class="pd-title">
                    <span>{{ productDetails.type }}</span>
                    <h3>{{ productDetails.name }}</h3>
                  </div>
                  <div class="pd-desc">
                    <p v-html="productDetails.description"></p>
                    <h4>${{ productDetails.price }}</h4>
                  </div>
                  <div class="quantity">
                    <!-- <router-link to="/cart"> -->
                    <a @click="saveKeranjang(productDetails.id, productDetails.name, productDetails.price, productDetails.galleries[0].photo)" href="#" class="primary-btn pd-cart">Add To Cart</a>
                    <!-- </router-link> -->
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Product Shop Section End -->
    <RelatedProduct />
    <FooterStore />
  </div>
</template>

<script>
import HeaderStore from "@/components/HeaderStore.vue";
import RelatedProduct from "@/components/RelatedProduct.vue";
import FooterStore from "@/components/FooterStore.vue";
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "ProductView",
  components: {
    HeaderStore,
    RelatedProduct,
    FooterStore,
    carousel,
  },
  data() {
    return {
      default_img: "",
      productDetails: [],
      keranjangUser: [],
    };
  },
  methods: {
    changeImg(src) {
      this.default_img = src;
    },
    setDataPicture(data) {
      // replace object productDetails dgn data dari API
      this.productDetails = data;
      // replace value img_default dgn data dari API (galleries)
      this.default_img = data.galleries[0].photo;
    },
    saveKeranjang(id, name, price, img) {
      var productStored = {
        id: id,
        name: name,
        price: price,
        img: img,
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
      .get("http://127.0.0.1:8000/api/products", {
        params: {
          id: this.$route.params.id,
        },
      })
      .then((res) => this.setDataPicture(res.data.data))
      // eslint-disable-next-line no-console
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.product-thumbs .pt {
  margin-right: 14px;
}
</style>
