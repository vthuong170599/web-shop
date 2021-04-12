<template>
  <div>
    <b-row>
      <b-col sm="4" class="search position-relative">
        <b-input
          placeholder="Enter your key word"
          class="search-input"
          v-model="keyword"
        ></b-input>
        <b-button class="btn-serach" @click="search"> search </b-button>
      </b-col>
      <!-- <b-col sm="1" class="search position-relative">
      </b-col> -->
    </b-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      keyword: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.keyword);
    },
  },
};
</script>
<style scoped>
.search {
  display: inline;
  margin-bottom: 1%;
}
.search-input {
  width: 80%;
}
.btn-serach {
  position: absolute;
  top: 0px;
  left: 78%;
}
</style>