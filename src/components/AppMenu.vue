<template>
  <button
    @click="showMenu = !showMenu"
    v-if="showBtn"
    id="menu-btn"
    title="Open Menu"
    class="btn btn-menu"
  >
    <span v-if="!showMenu">Menu</span>
    <i v-else class="fal fa-times"></i>
  </button>
  <aside v-if="showMenu" class="menu">
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
import { ref, onMounted, watch } from "vue";
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
    let showBtn = ref(true);
    let showMenu = ref(false);
    onMounted(() => {
      if (window.innerWidth > 1024) {
        showBtn.value = false;
        showMenu.value = true;
      }
    });

    return { items, showBtn, showMenu };
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
  border-radius: 8px;
  overflow: hidden;
  width: 264px;
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

@media screen and (max-width: 1024px) {
  .menu {
    position: absolute;
    top: calc(3vw + 34px);
    right: 20px;
  }
  .btn-menu {
    padding: 5px 10px;
    position: absolute;
    top: 3vw;
    font-size: 14px;
    right: 20px;
    margin: 0;
    transition: 0.3s;
    box-sizing: border-box;
    min-width: 55px;
    min-height: 34px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: $border-grey;
  }
}
</style>