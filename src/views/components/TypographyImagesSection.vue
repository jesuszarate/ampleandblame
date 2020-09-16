<template>
  <div class="wrapper">
    <div id="images">
      <div class="title">
        <h2>Shop</h2>
      </div>
      <div class="md-layout">
        <SfCollectedProduct
          :qty="productQty"
          :class="customClass"
          @input="productQty = $event"
          :image="image1"
          :image-width="imageWidth"
          :image-height="imageHeight"
          :title="title"
          :regular-price="regularPrice"
          :special-price="specialPrice"
        >
          <template #configuration>
            <div :style="{ margin: '1rem 0 0 0' }">
              <SfProperty name="Size" value="XS" />
              <SfProperty name="Color" value="white" />
            </div>
          </template>
          <template #actions>
            <SfButton class="sf-button--text desktop-only"
              >Save for later</SfButton
            >
          </template>
        </SfCollectedProduct>
      </div>
    </div>
  </div>
</template>

<script>
import { SfCollectedProduct } from "@storefront-ui/vue";
import { SfProperty } from "@storefront-ui/vue";
import { SfButton } from "@storefront-ui/vue";
export default {
  components: {
    SfCollectedProduct,
    SfProperty,
    SfButton
  },
  data() {
    return {
      image: require("@/assets/img/faces/avatar.jpg"),
      responsive: false,
      productQty: 1,
      image1: {
        mobile: { url: require("@/assets/img/productB.jpg")},
        desktop: { url: require("@/assets/img/productB.jpg") }
      },
      imageWidth: 140,
      imageHeight: 200,
      title: "Cotton Sweater",
      regularPrice: "$10,99",
      specialPrice: "$5,09"
    };
  },
  methods: {
    onResponsiveInverted() {
      if (window.innerWidth < 600) {
        this.responsive = true;
      } else {
        this.responsive = false;
      }
    }
  },
  mounted() {
    this.onResponsiveInverted();
    window.addEventListener("resize", this.onResponsiveInverted);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResponsiveInverted);
  }
};
</script>

<style lang="css"></style>
