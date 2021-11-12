<template>
  <div class="home">
    hi
    <ProductDescriptionDrawer
      :product="product"
      :active="active.product_drawer"
      @close-product-drawer="closeProductDrawer"
    />

    <div class="container">
      <div class="product-cards-list">
        <ProductSummaryCard
          v-for="product in items"
          :key="product.id"
          :product="product"
          @view-product="viewProduct($event)"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import items from "@/data/items.js";
import ProductSummaryCard from "@/components/ProductSummaryCard.vue";
import ProductDescriptionDrawer from "@/components/ProductDescriptionDrawer.vue";

export default Vue.extend({
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer,
  },
  data() {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false,
      },
    };
  },
  methods: {
    viewProduct(product: any) {
      this.product = product;
      this.active.product_drawer = true;
      console.log(this.product);
    },
    closeProductDrawer() {
      this.active.product_drawer = false;
    },
  },
  layout: "default",
  fetch() {},
});
</script>

<style lang="scss">
.product-cards-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>