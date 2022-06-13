<template>
  <div id="expert" class="expertise scroll-top d-flex jc-center ai-center my-5">
    <!-- 左邊三圓形 -->
    <leftThreeCircle
      ref="circle"
      @parentChangeSlide="triggerChangeSlide"
    ></leftThreeCircle>
    <!-- 右邊swiper 介紹 -->
    <rightSwiper
      ref="Intro"
      @parentChangeCircle="triggerChangeCircle"
    ></rightSwiper>
  </div>
</template>

<script>
import leftThreeCircle from "./LeftThreeCircle.vue";
import rightSwiper from "./RightSwiper.vue";

export default {
  components: {
    leftThreeCircle,
    rightSwiper,
  },
  methods: {
    triggerChangeSlide(index) {
      // 父组件通過$ref調用Intro中的事件方法
      this.$refs.Intro.changeSlide(index);
    },
    triggerChangeCircle(index) {
      // 父组件通過$ref調用circle中的事件方法
      this.$refs.circle.changeCircle(index);
    },
  },
};
</script>

<style scoped lang="scss">
@media all and (max-width: 1080px) {
  // 容器 變垂直排列
  .expertise {
    flex-direction: column;
  }
}
</style>