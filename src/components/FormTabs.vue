<template>
  <ul class="tabs__list">
    <li v-for="item in arr" :key="item.id" class="tabs__item">
      <button
        class="tabs__button"
        :class="{ tabs__button_active: item.title === this.activeTab }"
        @click="setActive"
      >
        {{ item.title }}
      </button>
    </li>
  </ul>
</template>
<script>
export default {
  data() {
    return {
      arr: [
        { id: 0, title: "Behavior" },
        { id: 1, title: "Appearance" },
        { id: 2, title: "Custom Fields" },
        { id: 3, title: "Questions" },
        { id: 4, title: "URL Control" },
      ],
      activeTab: "Behavior",
    };
  },
  methods: {
    setActive(e) {
      this.activeTab = e.target.textContent;
    },
  },
};
</script>
<style lang="scss">
.tabs {
  &__list {
    display: flex;
  }
  &__item {
  }
  &__button {
    font-weight: 600;
    font-size: 12px;
    line-height: 20px;
    letter-spacing: 0.03em;
    border: none;
    background-color: transparent;
    text-transform: uppercase;
    padding: 14px 16px;
    cursor: pointer;
    transition: 0.3s;
    box-sizing: border-box;
    height: 100%;
    border: 1px solid transparent;
    &:hover,
    &:focus {
      color: $green;
    }
  }
  &__button_active {
    color: $green;
    border: 1px solid $border-grey;
    border-bottom: 1px solid #fff;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
    box-sizing: border-box;
  }
}
</style>