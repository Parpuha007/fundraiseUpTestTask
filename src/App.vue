<template>
  <main>
    <div class="container">
      <app-search />
      <app-info />
    </div>
  </main>
</template>

<script>
import AppInfo from "./components/AppInfo.vue";
import AppSearch from "./components/AppSearch.vue";
export default {
  name: "App",
  components: { AppSearch, AppInfo },
};
</script>

<style lang="scss">
@import url("./assets/css/all.min.css");
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:wght@400;600&display=swap");
@import url("./assets/scss/_mixins.scss");
* {
  margin: 0;
  padding: 0;
}
ul,
ol,
dl {
  list-style: none;
}
img {
  display: flex;
  max-width: 100%;
}
input,
button {
  outline: none;
}
body {
  font-family: "Work Sans", sans-serif;
  background: #e5e5e5;
  color: $text-black;
}
.container {
  width: 1224px;
  margin: auto;
  padding-top: 53px;
  position: relative;
}
</style>
