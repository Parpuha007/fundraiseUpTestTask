<template>
  <section class="info">
    <div class="info__row info__top">
      <div class="info__left">
        <h6><span>Donation</span></h6>
        <div class="info__values">
          <span class="info__current-value">€20.60 EUR</span>
          <span class="info__converted-value">≈ $22.22 USD</span>
        </div>
      </div>
      <div class="info__right">
        <span class="info__id-text">ID</span>
        <div class="info__id-container">
          <span class="info__id-value">{{ id }} </span>
          <button class="info__copy-btn" @click="copyId">
            <i title="Copy to clipboard" class="fal fa-clone"></i>
          </button>
        </div>
      </div>
    </div>
    <div class="info__row info__bottom">
      <ul class="info__list">
        <li class="info__list-item status">
          <span class="name">Status</span>
          <span class="status__state"
            ><i class="fas fa-check-circle"></i> Success</span
          >
        </li>
        <info-list-item
          :info="{ name: 'Supporter', description: 'Charlotte Ann' }"
          class="info__list-item"
        />
        <info-list-item
          :info="{ name: 'Campaign', description: 'Workout for water' }"
          class="info__list-item"
        />
      </ul>
    </div>
  </section>
</template>
<script>
import InfoListItem from "./InfoListItem.vue";
export default {
  components: {
    InfoListItem,
  },
  data() {
    return {
      id: "DYHY694Y",
    };
  },
  methods: {
    copyId(e) {
      navigator.clipboard.writeText(this.id);
      e.target.blur();
    },
  },
};
</script>
<style lang="scss" scoped>
.info {
  @include sectionStyles;
  &__row {
    display: flex;
    justify-content: space-between;
  }
  &__top {
    padding: 24px 32px;
  }
  &__bottom {
    @include bottomInSections;
    padding: 16px 0 16px 32px;
  }
  &__left {
    h6 {
      position: relative;
      font-size: 14px;
      line-height: 20px;
      font-weight: normal;
      margin-bottom: 5px;
      padding-left: 26px;
      background: url(../assets/img/dollar.svg) no-repeat 0 50%;
    }
  }
  &__right {
    display: flex;
    flex-direction: column;
  }
  &__current-value {
    font-size: 24px;
    line-height: 32px;
    color: $green;
    margin-right: 8px;
  }
  &__converted-value {
    font-size: 16px;
    line-height: 24px;
    color: $grey;
  }
  &__id-text {
    color: #919293;
    margin-bottom: 4px;
    line-height: 20px;
  }
  &__id-value {
    font-size: 16px;
    line-height: 24px;
    .fa-clone {
      color: $grey;
      cursor: pointer;
      &:active {
        color: $green;
      }
    }
  }
  &__list {
    display: flex;
  }
  &__list-item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    .name {
      font-size: 14px;
      line-height: 20px;
      color: $grey;
    }
    &:not(:last-child) {
      border-right: 1px solid #d7d8da;
      padding-right: 32px;
      margin-right: 32px;
    }
  }
  &__copy-btn {
    border: none;
    cursor: pointer;
    background-color: transparent;
    margin-left: 9.5px;
    &:hover i {
      color: $green;
    }
  }
  &__id-container {
    display: flex;
    align-items: center;
  }
}
.fa-dollar-sign {
  color: $blue;
}
.status {
  &__state {
    font-size: 16px;
    line-height: 24px;
    color: $green;
  }
}
@media screen and (max-width: 768px) {
  .info {
    margin-bottom: 3vw;
  }
}
@media (max-width: 540px) {
  .info {
    &__list-item {
      &:not(:last-child) {
        padding-right: 5vw;
        margin-right: 5vw;
      }
    }
    &__top {
      padding: 3.5vw 4vw;
    }
    &__bottom {
      padding: 3vw;
      padding-left: 5vw;
    }
    &__current-value {
      font-size: 5vw;
      line-height: 6vw;
    }
    &__converted-value {
      font-size: 3.5vw;
      line-height: 6vw;
    }
    &__id {
      &-text,
      &-value {
        font-size: 14px;
      }
    }
  }
  .status__state {
    font-size: 3vw;
    line-height: 4.4vw;
  }
}
</style>