<template>
  <div id="app">
    <!-- <Header /> -->
    <div class="container">
      <router-view />
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
export default {
  // components: {
  //   Header
  // }
};
</script>

<style >
body {
  background: #222831;
}
.container {
  max-width: 900px;
}
.card {
  background: #1e1d24;
}
.card-body {
  color: #f9ffee;
}
.card-body a {
  color: #efbb35;
}
</style>
