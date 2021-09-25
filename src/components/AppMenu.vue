<template>
  <button v-if="hideMenu" class="btn show-btn">
    <i class="fal fa-bars"></i> MENU
  </button>
  <aside v-else class="menu">
    <nav>
      <ul class="menu__list">
        <li class="menu__item" v-for="item in items" :key="item.id">
          <button>
            <img :src="item.imagePath" alt="" /> <span>{{ item.title }}</span>
          </button>
        </li>
      </ul>
    </nav>
  </aside>
</template>
<script>
export default {
  setup() {
    const items = [
      {
        id: 0,
        title: "Change Amount",
        imagePath: require("../assets/img/repeat.svg"),
      },
      {
        id: 1,
        title: "Change Payment Method",
        imagePath: require("../assets/img/wallet.svg"),
      },
      {
        id: 2,
        title: "Change Date",
        imagePath: require("../assets/img/calendar.svg"),
      },
      {
        id: 3,
        title: "Cancel Recurring",
        imagePath: require("../assets/img/cancel.svg"),
      },
    ];
    let hideMenu = false;
    return { items, hideMenu };
  },
};
</script>
<style lang="scss" scoped>
.menu {
  position: sticky;
  top: 20px;
  right: 0;
  box-shadow: 1px 3px 3px rgba(62, 63, 64, 0.1);
  box-sizing: border-box;
  nav {
    width: 100%;
  }
  &__list {
    display: flex;
    flex-direction: column;
  }
  &__item {
    position: relative;

    &:not(:last-child) {
      border-bottom: 1px solid $border-grey;
    }
    &:first-child button {
      border-top-left-radius: 8px;
      border-top-right-radius: 8px;
    }
    &:last-child button {
      border-bottom-left-radius: 8px;
      border-bottom-right-radius: 8px;
    }
    button {
      background: #ffffff;
      width: 100%;
      transition: 0.3s;
      border: none;
      display: flex;
      align-items: center;
      font-size: 16px;
      line-height: 28px;
      padding: 12px 0 12px 16px;
      box-sizing: border-box;
      max-height: 52px;
      span {
        letter-spacing: 0.8px;
      }
      img {
        margin-right: 8px;
        width: 18px;
        height: 18px;
      }
      &:hover {
        background-color: #f3f3f3;
      }
    }
  }
}
</style>