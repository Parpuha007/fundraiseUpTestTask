<template>
  <section class="form-component">
    <form-tabs class="form-component__tabs" />
    <!-- <component :is='name'></component> в будущем -->
    <form-behavior class="form-component__behavior" />
  </section>
</template>
<script>
import FormBehavior from "./FormBehavior.vue";
import FormTabs from "./FormTabs.vue";
export default {
  components: {
    FormTabs,
    FormBehavior,
  },
};
</script>
<style lang="scss" scoped>
.form-component {
  padding-top: 32px;
  @include sectionStyles;
  &__tabs {
    padding-left: 24px;
  }
  &__behavior {
    border-top: 1px solid $border-grey;
    margin-top: -1px;
  }
}
@media screen and (max-width: 540px) {
  .form-component {
    padding-top: 3.5vw;
    overflow: hidden;
    &__tabs {
      padding: 0 10px;
    }
  }
}
</style>