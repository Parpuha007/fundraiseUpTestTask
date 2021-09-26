<template>
  <li>
    <span class="name">{{ info.name }}</span>
    <span class="description">{{ info.description }}</span>
  </li>
</template>
<script>
export default {
  props: ["info"],
};
</script>
<style lang="scss" scoped>
.name {
  font-size: 14px;
  line-height: 20px;
  color: $grey;
}
.description {
  font-size: 16px;
  line-height: 24px;
  color: $violet;
}
@media screen and (max-width: 540px) {
  .description {
    font-size: 3vw;
    line-height: 4.4vw;
  }
  .name {
    font-size: 2.8vw;
    line-height: 4vw;
  }
}
</style>