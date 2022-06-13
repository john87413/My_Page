<template>
  <!-- 容器 -->
  <div class="circle-content d-flex ai-center mx-5">
    <!-- 右邊白色圓圈 -->
    <div class="circle-right bg-white d-flex flex-column jc-center ai-center">
      <p class="title m-4 text-primary fs-xxxxl">3</p>
      <p class="text m-4 text-dark-grey fs-xl text-center">
        Years <br />
        Of Experience
      </p>
    </div>
    <!-- 左邊 背後藍色圓圈 -->
    <div class="circle-left bg-primary"></div>
  </div>
</template>


<script>
export default {};
</script>

<style scoped lang="scss">
// 容器
.circle-content {
  position: relative;
  width: 27rem;
  height: 27rem;
  // 右邊白色圓圈
  .circle-right {
    z-index: 1;
    border-radius: 50%;
    box-shadow: 0.7094rem 1.3922rem 1.62rem 0.0675rem rgba(14, 62, 129, 0.29);
    width: 80%;
    height: 80%;
  }
  // 左邊藍色圓圈
  .circle-left {
    position: absolute;
    border-radius: 50%;
    width: 70%;
    height: 70%;
    top: 8.5%;
    left: -22%;

    // 左邊藍色圓圈底部白色裝飾
    &::before {
      content: "";
      position: absolute;
      left: -8%;
      bottom: -21%;
      width: 79%;
      height: 82.5%;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.1);
    }
    // 左邊藍色圓圈底部白色裝飾
    &::after {
      content: "";
      position: absolute;
      left: 10%;
      bottom: -16%;
      width: 79%;
      height: 79%;
      border-radius: 50%;
      background-color: rgba(255, 255, 255, 0.15);
    }
  }
  // 容器右邊藍色圓圈裝飾
  &::after {
    content: "";
    position: absolute;
    right: 0;
    top: 0;
    width: 3.5rem;
    height: 3.5rem;
    background-color: #2c7ae7;
    border-radius: 50%;
    background: linear-gradient(to right, #2876e2 0, #3f8efc 100%);
  }
  // 容器右邊藍色圓圈裝飾
  &::before {
    content: "";
    position: absolute;
    right: 0;
    top: 5.6rem;
    width: 2.5rem;
    height: 2.5rem;
    background-color: #2c7ae7;
    border-radius: 50%;
    background: linear-gradient(to right, #2876e2 0, #3f8efc 100%);
  }
}

@media all and (max-width: 1080px) {
  // 容器
  .circle-content {
    margin-right: 0;
    margin-left: 5rem;
  }
}

@media all and (max-width: 590px) {
  // 容器
  .circle-content {
    width: 24rem;
    height: 24rem;
  }
}
@media all and (max-width: 400px) {
  // 容器
  .circle-content {
    width: 18.5rem;
    height: 18.5rem;
    .circle-right {
      .title {
        margin: 1rem;
        font-size: 5rem;
      }
      .text {
        margin: 1rem;
        font-size: 1.3rem;
      }
    }
  }
}
</style>