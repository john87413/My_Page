<template>
  <div class="footer-right d-flex ai-center jc-center">
    <img class="white-logo" src="../../assets/images/self-logo-white.png" />
    <p class="right-info text-white d-flex jc-end">
      © 2019 Self. All rights reserved.
    </p>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";
.footer-right {
  height: 6rem;
  border-top: 1px solid map-get($colors, "light-grey");
  .white-logo {
    width: 7rem;
    height: 2.5rem;
  }
  .right-info {
    width: 43rem;
  }
}

// 布局改垂直 高度增加
@media all and (max-width: 900px) {
  .footer-right {
    flex-direction: column;
    .white-logo {
      width: 7rem;
      height: 2.5rem;
    }
    .right-info {
      width: fit-content;
      margin-top: 0.2rem;
    }
  }
}
</style>