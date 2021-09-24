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
</style>