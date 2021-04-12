<template>
  <div>
    <list-product :dataProduct="dataProduct" />
  </div>
</template>
<script>
import ListProduct from "../../components/Product/ListProduct.vue";
import axios from "axios";
import { URL } from "../../constant/constant";
export default {
  components: { ListProduct },
  data() {
    return {
      dataProduct: [],
      pages: {},
      currentPage: 1,
    };
  },
  methods: {
      /**
       * get product by category
       * @param Integer category id
       */
    getProductByCategory(cate_id){
        axios.get(URL+"product_by_category/"+cate_id).then(res=>{
            this.dataProduct = res.data.data
        })
    }
  },
  mounted() {
    this.getProductByCategory(this.$route.params.category);
  },
};
</script>