<template>
  <div>
    <b-card no-body class="overflow-hidden" style="max-width: 540px">
      <b-row no-gutters>
        <b-col md="6">
          <b-card-img
            :src="'http://localhost:8000/' + dataProduct.thumb"
            alt="Image"
            class="rounded-0"
          ></b-card-img>
        </b-col>
        <b-col md="6">
          <b-card-body :title="dataProduct.name">
            <div v-if="dataProduct.discount > 0">
              <b-card-text
                >price:
                {{ formatPrice(dataProduct.sale_price) }} VND</b-card-text
              >
              <b-card-text class="price"
                >{{ formatPrice(dataProduct.price) }} VND</b-card-text
              >
            </div>
            <div v-else>
              <b-card-text
                >{{ formatPrice(dataProduct.price) }} VND</b-card-text
              >
            </div>
            <b-card-text
              >category: {{ getCategory(dataProduct.categories) }}</b-card-text
            >
          </b-card-body>
        </b-col>
      </b-row>
    </b-card>
    <b-row class="footer">
      <b-col sm="6" class="qty">
        <b-button @click="reduction" class="reduction">-</b-button>
        <b-input v-model="qty"></b-input>
        <b-button @click="increase" class="increase">+</b-button>
      </b-col>
      <b-col sm="6" style="width: 100%">
        <b-button variant="danger">add to card</b-button>
      </b-col>
    </b-row>

    <b-row>
      <h3>desccription</h3>
    </b-row>
    <b-row>
      <p>{{ dataProduct.desc }}</p>
    </b-row>
  </div>
</template>
<script>
export default {
  props: {
    dataProduct: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      qty: 1,
    };
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

    formatPrice(price) {
      return Number.parseFloat(price).toFixed(2);
    },

    reduction() {
      this.qty--;
      if (this.qty <= 0) {
        this.qty = 1;
      }
    },

    increase() {
      this.qty++;
      if (this.qty > this.dataProduct.qty) {
        this.qty = this.dataProduct.qty;
      }
    },
  },
};
</script>
<style scoped>
.footer {
  margin-top: 10px;
}
.qty {
  width: 100%;
}
.qty input {
  width: 20%;
  text-align: center;
}
.price {
  text-decoration: line-through;
}
.reduction {
  float: left;
}
.increase {
  position: absolute;
  top: 0;
  left: 30%;
}
</style>