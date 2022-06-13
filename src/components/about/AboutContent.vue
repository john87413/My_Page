<template>
  <div class="about-container d-flex flex-column ai-center pt-3 px-4 mx-3">
    <!-- 方塊頂部icon -->
    <div class="about-icon d-flex ai-center jc-center">
      <i :class="`iconfont fs-xxxl text-white icon-${content.icon}`"></i>
    </div>
    <!-- 標題 -->
    <h4 class="about-title text-dark-grey fs-xl fw-bold my-3">
      {{ content.title }}
    </h4>
    <!-- 文字 -->
    <p
      class="about-text text-light-grey fs-lgs text-center"
      v-html="content.text"
    ></p>
  </div>
</template>

<script>
export default {
  props: ["content"],
};
</script>

<style lang="scss">
@import "../../assets/scss/variables.scss";
.about-container {
  position: relative;
  overflow: hidden;
  width: 22rem;
  height: 22rem;
  background-color: white;
  border: 0.0625rem solid map-get($colors, "light-grey-2");
  border-radius: 0.625rem;
  transition: background-color 0.4s ease;

  // 方塊下icon樣式
  .about-icon {
    width: 8rem;
    height: 8rem;
    border-radius: 50%;
    background: linear-gradient(
      to right,
      map-get($colors, "primary") 0,
      map-get($colors, "light-blue") 100%
    );
  }
  // 方塊右下角裝飾
  &::after {
    content: "";
    position: absolute;
    right: 0px;
    bottom: 0px;
    width: 0px;
    height: 0px;
    border-radius: 50%;
    background-color: map-get($colors, "white-2");
    opacity: 0;
    transition: all 0.4s ease;
  }
  // 方塊右下角裝飾
  &::before {
    content: "";
    position: absolute;
    right: 0px;
    bottom: 0px;
    width: 0px;
    height: 0px;
    border-radius: 50%;
    background-color: map-get($colors, "white-3");
    opacity: 0;
    transition: all 0.4s ease;
  }
  // 三方塊下 觸發樣式
  &:hover {
    background-color: map-get($colors, "primary");
    box-shadow: 0.3125rem 0.3125rem 0.775rem 0.2875rem
      map-get($colors, "light-black");
    // 方塊右下角裝飾
    &::after {
      opacity: 1;
      width: 20rem;
      height: 20rem;
      right: -11rem;
      bottom: -10rem;
    }
    // 方塊右下角裝飾
    &::before {
      opacity: 1;
      width: 22.5rem;
      height: 22.5rem;
      right: -10rem;
      bottom: -12rem;
    }

    // 三方塊下icon
    .about-icon {
      background: map-get($colors, "white");
      i {
        color: map-get($colors, "primary");
      }
    }
    // 三方塊下內容
    .about-title {
      color: map-get($colors, "white");
    }
    .about-text {
      color: map-get($colors, "white");
      a {
        color: map-get($colors, "white");
      }
      strong {
        color: map-get($colors, "white");
      }
    }
  }
}

@media all and (max-width: 1190px) {
  // 三方塊
  .about-container {
    width: 20rem;
  }
}

@media all and (max-width: 1080px) {
  .about-container {
    width: 22rem;
    &:nth-child(3) {
      width: 46rem;
      height: 19rem;
      margin-top: 1rem;
    }
  }
}
@media all and (max-width: 800px) {
  // 三方塊
  .about-container {
    width: 40rem;
    height: 18rem;
    margin-top: 1rem;
    &:nth-child(1){
      margin-top: 0;
    }
    &:nth-child(3) {
      width: 40rem;
      height: 18rem;
    }
    // 三方塊下icon
    .about-icon {
      width: 7rem;
      height: 7rem;
    }
  }
}
</style>