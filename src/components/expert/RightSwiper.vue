<template>
  <div class="expertise-swiper-container mx-2">
    <!-- 標題區 -->
    <myExpertTitle
      class="expertise-title ml-5 mb-3"
      v-bind:content="titleContent"
    ></myExpertTitle>
    <!-- 下面滑塊區 -->
    <div class="d-flex">
      <!-- 小icon -->
      <i class="iconfont icon-quote text-primary fs-xlx mt-3"></i>
      <!-- 滑塊 -->
      <swiper
        ref="list"
        class="swiper-expertise m-3 bg-light-grey-1"
        :options="swiperOption"
      >
        <swiper-slide
          class="
            swiper-slide-expertise
            d-flex
            flex-column
            ai-center
            jc-center
            p-4
          "
          v-for="(item, index) in introContents"
          :key="index"
        >
          <!-- 內容區 -->
          <p class="title fs-xxl text-dark-grey py-2">{{ item.title }}</p>
          <p class="text fs-lg text-light-grey py-2 text-center">
            {{ item.text }}
          </p>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
import myExpertTitle from "../title/Title.vue";

export default {
  components: {
    Swiper,
    SwiperSlide,
    myExpertTitle,
  },
  data() {
    return {
      // 標題
      titleContent: { title: "專長", text: "what do I expert in" },
      // 內容
      introContents: [
        {
          title: "教案設計",
          text: "大二時擔任了系上的學系服務學習助教，親自設計課程帶領學生去麥米羅幼兒園進行不插電程式教育，後來還在核果資訊學苑擔任過程式設計講師，負責網頁程式和Python + Line bot機器人的教學，這些經驗都讓我一次一次瞭解到規劃完整的課程需要兼顧內容深入淺出又有趣,課堂上的掌握度和細心度也是非常重要的",
        },
        {
          title: "網頁前端",
          text: "在網頁開發方面，個人比較擅長的是前端開發，曾開發過自己的個人網站和後台管理平台，而在這過去的開發經驗中，也讓我學習到了許多工具與技術的運用，像是HTML、SCSS、Vue.js、Node.js、ElementUI，還有RESTful API、測試與開發API的Postman、套件管理工具npm、非關聯式資料庫等等",
        },
        {
          title: "APP前端",
          text: "在APP開發方面，幾乎都是與別人合作開發，像是大三的團體專題以及與中正大學高齡中心的合作專案，而在這兩項專案中，個人負責的都是前端的部分，主要就是以JAVA和XML完成畫面製作、資料處理、API串接、訊息推播等等。",
        },
      ],
      swiperOption: {
        autoplay: {
          delay: 4000,
        },
        initialSlide: 1,
        on: {
          slideChange: () => {
            let swiper = this.$refs.list.$swiper;
            this.$emit("parentChangeCircle", swiper.activeIndex); //監聽從父子見傳過來的兄弟組件方法
          },
        },
      },
    };
  },
  methods: {
    //   給父組件調用的方法(threeCircle 組件才可調用)
    changeSlide(index) {
      this.$refs.list.$swiper.slideTo(index);
    },
  },
};
</script>

<style lang="scss">
@import "../../assets/scss/variables.scss";
// 滑塊容器
.swiper-expertise {
  border: 1px solid map-get($colors, "light-grey-2");
  border-radius: 10px;
  width: 35rem;
  height: 20rem;
  cursor: pointer;
}
@media all and (max-width: 1080px) {
  .expertise-swiper-container {
    // 標題
    .expertise-title {
      margin: 1.5rem 0;
      width: fit-content;
      text-align: start;
      div {
        font-size: 1.2rem;
      }
    }
  }
}
@media all and (max-width: 800px) {
  .expertise-swiper-container {
    // 滑塊
    .swiper-expertise {
      width: 29rem;
      height: 19rem;
    }
    i {
      font-size: 1.5rem;
    }
  }
}
@media all and (max-width: 590px) {
  .expertise-swiper-container {
    // 滑塊
    .swiper-expertise {
      width: 26rem;
      margin: 0;
    }
    i {
      display: none;
    }
  }
}
@media all and (max-width: 400px) {
  .expertise-swiper-container {
    // 滑塊
    .swiper-expertise {
      width: 23rem;
      height: 20rem;
      margin: 0;
      .swiper-slide-expertise {
        .title {
          font-size: 2rem;
        }
        .text {
          padding: 0 1rem;
          margin: 0;
          font-size: 1.2rem;
        }
      }
    }
  }
}
</style>