<template>
  <section class="search">
    <h1 class="search__heading">Donations</h1>
    <div class="search__row">
      <div class="search__input-wrapper">
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
        <button @click="toggleList" class="search__drop-btn">
          All statuses <i id="menu-icon" class="fal fa-angle-down"></i>
        </button>
        <ul v-if="showDropdown" id="drop-list" class="search__drop-list">
          <li><button>Status 1</button></li>
          <li><button>Status 2</button></li>
          <li><button>Status 3</button></li>
          <li><button>Status 4</button></li>
        </ul>
      </div>
    </div>
  </section>
</template>
<script>
import { ref } from "vue";
export default {
  emits: ["showMenu"],
  setup() {
    let searchValue = ref("");
    let showDropdown = ref(false);
    const toggleList = () => {
      showDropdown.value = !showDropdown.value;
      document.getElementById("menu-icon").classList.toggle("rotate-icon");
    };

    return {
      searchValue,
      showDropdown,
      toggleList,
    };
  },
};
</script>
<style lang="scss" scoped>
// @import url("../assets/scss/_mixins.scss");
.search {
  position: relative;
  @include sectionStyles;
  margin-bottom: 24px;
  border-top: none;
  &__drop {
    position: relative;
    display: flex;
    flex-grow: 1;
  }
  &__drop-list {
    position: absolute;
    left: 80px;
    top: 0;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    border: 1px solid $border-grey;
    border-radius: 8px;
    background-color: #fff;
    transition: 0.3s;
    z-index: 99;
    li {
      box-sizing: border-box;
      border-bottom: 1px solid $border-grey;
      position: relative;
      button {
        background-color: transparent;
        border: none;
        width: 100%;
        height: 100%;
        padding: 10px 15px;
        cursor: pointer;
      }
    }
  }
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
    position: relative;
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
    background: url(../assets/img/search.svg) no-repeat 16px 50%;
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
  &__drop-btn {
    cursor: pointer;
    transition: 0.3s;
    border: none;
    background-color: transparent;
    user-select: none;
    &:hover,
    &:focus {
      color: $green;
    }
    &:target {
      outline: 1px solid $green;
    }
  }
}
#menu-icon {
  transition: 0.3s;
}
.rotate-icon {
  transform: rotate(180deg);
}
@media screen and (max-width: 768px) {
  .search {
    margin-bottom: 3vw;
    &__heading {
      padding: 3.5vw 0 3.5vw 4vw;
    }
    &__row {
      padding: 3.5vw 0 3.5vw 4vw;
    }
    &__input {
      width: 60vw;
    }
    &__input-wrapper {
      margin-right: 5vw;
    }
    &__drop-list {
      left: unset;
      right: 0;
      top: 20px;
    }
  }
}
</style>