<template>
  <main>
    <app-search class="search-component" />
    <div class="row">
      <app-info class="info-component" />
      <app-form class="form-component" />
    </div>
  </main>
</template>

<script>
import AppForm from "./components/AppForm.vue";
import AppInfo from "./components/AppInfo.vue";
import AppSearch from "./components/AppSearch.vue";
export default {
  name: "App",
  components: { AppSearch, AppInfo, AppForm },
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
  padding-top: 53px;
}
.search-component {
  max-width: 1224px;
  margin: 0 auto;
}
.row {
  display: flex;
  margin: 0 auto;
  max-width: 1224px;
  flex-flow: column nowrap;
}
.info-component {
  // flex-basis: 936px;
  max-width: 936px;
  margin-bottom: 24px;
}

.form-component {
  max-width: 936px;
}
</style>
