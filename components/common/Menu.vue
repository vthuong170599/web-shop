<template>
  <div>
    <h4>Category</h4>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-for="(category, index) in listCategory"
        :key="index"
      >
        <nuxt-link :to="`/category-product/${category.id}`">{{
          category.name
        }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from "axios";
import { URL } from "../../constant/constant";
export default {
  data() {
    return {
      listCategory: [],
    };
  },
  methods: {
    getCategory() {
      axios.get(URL + "category").then((res) => {
        this.listCategory = res.data.data;
      });
    },
  },
  mounted() {
    this.getCategory();
  },
};
</script>
<style scoped>
li {
  text-align: center;
}
</style>