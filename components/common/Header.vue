<template>
  <div class="row">
    <div class="col-md-3 logo">
      <img src="../../static/logo.png" alt="" />
    </div>
    <div class="col-md-9 menu">
      <ul>
        <li><nuxt-link to="/">home</nuxt-link></li>
        <li><a href="">checkout</a></li>
        <li><a href="">card</a></li>
        <li><nuxt-link to="/login">login</nuxt-link></li>
      </ul>
    </div>
  </div>
</template>
<style scoped>
.row {
  width: 100%;
}
#header {
  margin-bottom: 20px;
}
img {
  width: 100px;
}
h1 {
  margin-left: 30%;
  width: 100%;
  margin-top: 2%;
}
.menu {
  margin-top: 20px;
}
.menu ul {
  margin-right: 30%;
  text-align: center;
  list-style: none;
}
.menu ul li {
  display: inline-block;
}
.menu ul li a {
  margin-left: 10px;
}
</style>