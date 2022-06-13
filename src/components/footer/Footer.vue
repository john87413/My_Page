<template>
  <div id="contact" class="my-footer scroll-top bg-dark-grey w-100">
    <contact></contact>
    <right></right>
  </div>
</template>

<script>
import contact from "./FooterContact.vue";
import right from "./FooterRight.vue";

export default {
  components: {
    contact,
    right,
  },
};
</script>

<style lang="scss" scoped>
// footer 容器 用 fix讓它可以像隱藏起來
.my-footer {
  z-index: -10;
  position: fixed;
  bottom: 0px;
}
// 小於900px後讓她不用被隱藏 不然可能會被遮到
@media all and (max-width: 900px) {
  .my-footer {
    position: static;
  }
}
</style>