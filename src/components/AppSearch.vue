<template>
  <section class="search">
    <h1 class="search__heading">Donations</h1>
    <div class="search__row">
      <div class="search__input-wrapper">
        <i class="fal fa-search search__magnifier-icon"></i>
        <input
          v-model="searchValue"
          class="search__input"
          type="search"
          placeholder="Search"
        />
        <i
          v-if="searchValue.length > 0"
          @click="searchValue = ''"
          class="fal fa-times search__clear-input"
        ></i>
      </div>
      <div class="search__drop">
        All statuses <i class="fal fa-angle-down"></i>
      </div>
      <ul class="search__statuses">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
      </ul>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      searchValue: "",
    };
  },
};
</script>
<style lang="scss" scoped>
// @import url("../assets/scss/_mixins.scss");
.search {
  @include sectionStyles;
  margin-bottom: 24px;
  &__heading {
    font-weight: normal;
    font-size: 24px;
    line-height: 32px;
    padding: 28px 0 28px 32px;
  }
  &__row {
    @include bottomInSections;
    display: flex;
    align-items: center;
    padding: 16px 0 16px 32px;
  }
  &__input {
    width: 336px;
    height: 40px;
    text-indent: 42px;
    font-size: 16px;
    line-height: 24px;
    border: 1px solid $border-grey;
    box-sizing: border-box;
    border-radius: 8px;
    transition: 0.3s;
    &:focus {
      border: 1px solid $green;
    }
    &::-webkit-search-cancel-button {
      display: none;
    }
    &::placeholder {
      color: $grey;
    }
  }
  &__input-wrapper {
    position: relative;
    margin-right: 40px;
  }
  &__magnifier-icon {
    left: 16px;
    @include searchIconStyles;
  }
  &__clear-input {
    right: 10px;
    @include searchIconStyles;
    cursor: pointer;
    &:hover {
      color: $green;
    }
  }
  &__drop {
    cursor: pointer;
    transition: 0.3s;
    &:hover {
      color: $green;
    }
  }
  &__statuses {
    display: none;
  }
}
</style>