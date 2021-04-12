<template>
  <b-row>
    <b-col md="4" v-for="(product, index) in dataProduct" :key="index">
      <b-card
        :title="product.name"
        :img-src="'http://localhost:8000/' + product.thumb"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem"
        class="mb-2"
      >
        <div v-if="product.discount > 0">
          <b-card-text
          >price:
          {{ formatPrice(product.sale_price) }}
          VND (-{{product.discount}}%)</b-card-text
        >
          <b-card-text class="price"
          >
          {{ formatPrice(product.price) }}
          VND</b-card-text
        >
        </div>
        <b-card-text
          >category: {{ getCategory(product.categories) }}
        </b-card-text>
        <b-button variant="primary" @click="viewDetail(product.id)"
          >view detail</b-button
        >
      </b-card>
    </b-col>
  </b-row>
</template>
<script>
export default {
  props: {
    dataProduct: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    /**
     * get category name
     * @param Object category
     */
    getCategory(category) {
      if (category == null) {
        return false;
      }
      return category.name;
    },

    viewDetail(id) {
      this.$router.push(`/product/${id}`);
    },

    formatPrice(price) {
      return Number.parseFloat(price).toFixed(2);
    },
  },
};
</script>
<style scoped>
.price{
  text-decoration: line-through;
}
</style>