<template>
  <swiper id="mySwiper" class="my-swiper" :options="swiperOption">
    <swiper-slide
      class="d-flex ai-center jc-center"
      v-for="(item, index) in contents"
      :key="index"
    >
      <my-swiper-content v-bind:sigleContent="item"></my-swiper-content>
    </swiper-slide>
    <div class="swiper-pagination pagination-home mb-3" slot="pagination"></div>
  </swiper>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

import MySwiperContent from "./MySwiperContent.vue";

export default {
  components: {
    Swiper,
    SwiperSlide,
    "my-swiper-content": MySwiperContent,
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
      },
      // swiper 內容區
      contents: [
        {
          title: "Hello",
          subTitle: "I'm John",
          text: "我是一名軟體開發者，擅長的領域是網頁與APP開發，個人特色是勇於嘗試樂於學習，喜歡新奇有趣的事情。",
        },
        {
          title: "Web",
          subTitle: "Developer",
          text: "曾開發過兩個個人網站和一個後台管理平台，從中學習的技術有Vue.js、ElementUI、express.js、Axios、mongoDB、CRUD、JWT等等。",
        },
        {
          title: "APP",
          subTitle: "Developer",
          text: "大三時與同學一起協助校內高齡中心開發東石在地資訊平台，協助長照人員快速融入當地環境。",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
@import "../../assets/scss/variables.scss";
.my-swiper {
  padding-top: 4rem;
  height: 100vh;
  .swiper-slide {
    background-size: cover;
    background-position: center;
    &:nth-child(1) {
      background-image: url("../../assets/images/self-bg.jpg");
    }
    &:nth-child(2) {
      background-image: url("../../assets/images/web-bg.jpg");
    }
    &:nth-child(3) {
      background-image: url("../../assets/images/app-bg.jpg");
    }
    // 滑欄上面的遮罩
    &::after {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background-color: map-get($colors, "white-1");
    }
  }

  // 底部三個點點
  .pagination-home {
    .swiper-pagination-bullet {
      width: 0.625rem;
      height: 0.625rem;
      margin: 0 0.625rem;
      background: #303036;
      opacity: 1;
      transition: all 0.3s ease;
      &:hover {
        background: map-get($colors, "primary");
      }
    }
    .swiper-pagination-bullet-active {
      width: 0.8125rem;
      height: 0.8125rem;
      background: map-get($colors, "primary");
      transition: all 0.3s ease;
    }
  }
}
</style>
