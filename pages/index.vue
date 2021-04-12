<template>
  <div>
    <search @search="search"/>
    <list-product :dataProduct="dataProduct" />
    <b-pagination
      v-if="checkPaginate"
      v-model="currentPage"
      :total-rows="pages.total"
      :per-page="pages.per_page"
      @page-click="getProduct"
      prev-text="Prev"
      next-text="Next"
    ></b-pagination>
  </div>
</template>
<script>
import ListProduct from "../components/Product/ListProduct.vue";
import axios from "axios";
import { URL } from "../constant/constant";
import Search from "../components/common/search.vue";
export default {
  components: { ListProduct, Search },
  data() {
    return {
      dataProduct: [],
      pages: {},
      currentPage: 1,
      checkPaginate: true
    };
  },
  methods: {
    /**
     * get all product
     */
    getProduct(e, page) {
      axios.get(URL + "product?page=" + page).then((res) => {
        this.dataProduct = res.data.data;
        this.pages = res.data.meta;
      });
    },

    search(data){
      if(data == ""){
        return this.getProduct();
      }
      axios.get(URL+'search_product?name='+data).then(res=>{
        this.dataProduct = res.data.data
        this.checkPaginate = false
      })
    },

    showPaginate(){
      if(pages.last_page > 1){
        this.checkPaginate = !this.checkPaginate
      }
    }
  },
  mounted() {
    this.getProduct();
  },
};
</script>