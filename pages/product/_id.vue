<template>
  <product-detail :dataProduct="dataProduct" />
</template>
<script>
import ProductDetail from "../../components/Product/ProductDetail";
import axios from "axios";
import { URL } from "../../constant/constant";
export default {
  components: { ProductDetail },
  data() {
    return {
      dataProduct: {},
    };
  },
  methods: {
    getProduct(id) {
      axios.get(URL + "product/" + id).then((res) => {
          this.dataProduct = res.data.data
      });
    },
  },
  mounted(){
      this.getProduct(this.$route.params.id);
  }
};
</script>