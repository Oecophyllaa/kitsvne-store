<template>
  <div class="product">
    <HeaderStore />
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="breadcrumb-text product-more">
              <a href="./home.html"><i class="fa fa-home"></i> Home</a>
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
                  <img class="product-big-img" src="img/products/mickey1.jpg" alt="" />
                </div>
                <div class="product-thumbs">
                  <carousel class="product-thumbs-track ps-slider" :dots="false" :nav="false" :autoplay="true" :loop="true">
                    <div class="pt active" data-imgbigurl="img/products/mickey1.jpg">
                      <img src="img/products/mickey1.jpg" alt="" />
                    </div>

                    <div class="pt" data-imgbigurl="img/products/mickey2.jpg">
                      <img src="img/products/mickey2.jpg" alt="" />
                    </div>

                    <div class="pt" data-imgbigurl="img/products/mickey3.jpg">
                      <img src="img/products/mickey3.jpg" alt="" />
                    </div>

                    <div class="pt" data-imgbigurl="img/products/mickey4.jpg">
                      <img src="img/products/mickey4.jpg" alt="" />
                    </div>
                  </carousel>
                </div>
              </div>
              <div class="col-lg-6">
                <div class="product-details">
                  <div class="pd-title">
                    <span>oranges</span>
                    <h3>Pure Pineapple</h3>
                  </div>
                  <div class="pd-desc">
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis, error officia. Rem aperiam laborum voluptatum vel, pariatur modi hic provident eum iure natus quos non a sequi, id accusantium! Autem.</p>
                    <p>
                      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quam possimus quisquam animi, commodi, nihil voluptate nostrum neque architecto illo officiis doloremque et corrupti cupiditate voluptatibus error illum.
                      Commodi expedita animi nulla aspernatur. Id asperiores blanditiis, omnis repudiandae iste inventore cum, quam sint molestiae accusamus voluptates ex tempora illum sit perspiciatis. Nostrum dolor tenetur amet, illo
                      natus magni veniam quia sit nihil dolores. Commodi ratione distinctio harum voluptatum velit facilis voluptas animi non laudantium, id dolorem atque perferendis enim ducimus? A exercitationem recusandae aliquam quod.
                      Itaque inventore obcaecati, unde quam impedit praesentium veritatis quis beatae ea atque perferendis voluptates velit architecto?
                    </p>
                    <h4>$495.00</h4>
                  </div>
                  <div class="quantity">
                    <a href="shopping-cart.html" class="primary-btn pd-cart">Add To Cart</a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- Product Shop Section End -->
    <FooterStore />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderStore from "@/components/HeaderStore.vue";
import FooterStore from "@/components/FooterStore.vue";
import carousel from "vue-owl-carousel";

export default {
  name: "ProductView",
  components: {
    HeaderStore,
    FooterStore,
    carousel,
  },
};
</script>

<style scoped>
.product-thumbs .pt {
  margin-right: 14px;
}
</style>
