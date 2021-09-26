<template>
  <main>
    <app-search class="search-component" />
    <div class="row">
      <app-info class="info-component" />
      <app-menu class="menu-component" />
      <app-form class="form-component" />
    </div>
  </main>
</template>

<script>
import AppForm from "./components/AppForm.vue";
import AppInfo from "./components/AppInfo.vue";
import AppSearch from "./components/AppSearch.vue";
import AppMenu from "./components/AppMenu.vue";
export default {
  name: "App",
  components: { AppSearch, AppInfo, AppForm, AppMenu },
  methods: {
    tabFocus(e) {
      if (e.code === "Tab") {
        if (e.target.type === "radio" || e.target.type === "checkbox") {
          e.target.labels[0].classList.add("selectedElement");
        }
        document.activeElement.classList.add("selectedElement");
      }
    },
    tabUnfocus(e) {
      e.target.classList.remove("selectedElement");
      if (e.target.type === "radio" || e.target.type === "checkbox") {
        e.target.labels[0].classList.remove("selectedElement");
      }
    },
  },
  mounted() {
    document.addEventListener("keyup", this.tabFocus, false);
    document.addEventListener("focusout", this.tabUnfocus, false);
  },
};
</script>

<style lang="scss">
:root {
  --container-width: 1224px;
}
@import url("./assets/css/all.min.css");
@import url("https://fonts.googleapis.com/css2?family=Work+Sans:wght@400;600&display=swap");
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
  padding: 50px 0;
  font-size: 16px;
  line-height: 24px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
main {
  position: relative;
  margin: 0 auto;
  max-width: var(--container-width);
  width: 96%;
}
.search-component {
  width: 100%;
  margin: 0 auto;
}
.info-component {
  // width: 76.5%;
  flex-basis: 76.5%;
  max-width: 936px;
  margin-bottom: 24px;
  // flex-grow: 0;
}

.form-component {
  flex-basis: 76.5%;
  max-width: 936px;
}
.menu-component {
  // width: 21.6%;
  max-width: 264px;
  display: flex;
  flex-grow: 1;
  flex-basis: 21.6%;
}
.selectedElement {
  box-shadow: 0px 0px 2px 1px $violet !important;
}
.row {
  position: relative;
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: flex-start;
}
@media (max-width: 1200px) {
  .info-component,
  .form-component {
    flex-basis: calc(100% - 288px);
  }
}
@media (max-width: 1024px) {
  .form-component,
  .info-component {
    flex-basis: 100%;
    max-width: unset;
  }
  .row {
    position: static;
  }
}
@media screen and (max-width: 768px) {
  body {
    padding: 2vw 0;
  }
}
</style>
