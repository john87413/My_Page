<template>
  <!-- 容器 水平排列 並分開 -->
  <div class="auto-content bg-light-grey-1 py-5 d-flex jc-around ai-center">
    <p class="fs-xxl">自傳與簡歷</p>
    <button class="bt-1 bt-back-1 bt-nav-1 ripple fs-xl py-2 fw-bold" @click="showAlert">
      查看/下載(PDF)
    </button>
  </div>
</template>

<script>
export default {
  methods: {
    showAlert() {
      window.open("https://www.cakeresume.com/johnnew", '_blank').focus();
    },
  },
};
</script>

<style scoped lang="scss">
.auto-content {
  button {
    width: 15rem;
  }
}
@media all and (max-width: 800px) {
  // 容器改垂直排列
  .auto-content {
    flex-direction: column;
    button {
      margin-top: 2rem;
    }
  }
}
</style>