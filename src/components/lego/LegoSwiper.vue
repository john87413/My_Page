<template>
  <swiper ref="list" class="swiper-lego pt-3 pb-4" :options="swiperOption">
    <swiper-slide
      class="lego-slide d-flex jc-center fl-wrap"
      v-for="(legoList, index) in legoConotents"
      :key="index"
    >
      <!-- 一個slide有三個卡片 -->
      <div
        class="lego-card d-flex flex-column ai-center m-2 mb-4"
        v-for="(item, index) in legoList.legoItem"
        :key="index"
      >
        <!-- 卡片圖片 -->
        <img class="lego-img w-100" :src="item.imgSrc" />
        <!-- 卡片日期 -->
        <div class="lego-date fs-xxs bg-primary text-white py-1 px-2">
          {{ item.date }}
        </div>
        <!-- 卡片標題 -->
        <div class="lego-title text-dark-grey fw-bold fs-lg mx-2 my-2">
          {{ item.title }}
        </div>
        <!-- 卡片內文 -->
        <p class="lego-text text-light-grey mx-3 text-center">
          {{ item.text }}
        </p>
      </div>
    </swiper-slide>
    <div
      class="swiper-pagination lego-pagination text-white"
      slot="pagination"
    ></div>
  </swiper>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

import lego1 from "../../assets/images/lego-1.jpg";
import lego2 from "../../assets/images/lego-2.jpg";
import lego3 from "../../assets/images/lego-3.jpg";
import lego4 from "../../assets/images/lego-4.jpg";
import lego5 from "../../assets/images/lego-5.jpg";
import lego6 from "../../assets/images/lego-6.jpg";
import lego7 from "../../assets/images/lego-7.jpg";
import lego8 from "../../assets/images/lego-8.jpg";
import lego9 from "../../assets/images/lego-9.jpg";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          renderBullet(index, className) {
            return `<span class="${className}">${index + 1}</span>`;
          },
        },
      },
      legoConotents: [
        {
          legoItem: [
            {
              imgSrc: lego1,
              date: "04 / 01 / 2019",
              title: "崇文國小-創意樂高",
              text: "高年級的小朋友做的一台手動車，這位同學非常認真而且有創意。",
            },
            {
              imgSrc: lego2,
              date: "04 / 14 / 2019",
              title: "崇文國小-創意樂高",
              text: "很Q的小型挖土機，小朋友還會帶自己家裡的樂高來玩。",
            },
            {
              imgSrc: lego3,
              date: "04 / 26 / 2019",
              title: "崇文國小-創意樂高",
              text: "小朋友做的一台升降車，非常厲害喔。",
            },
          ],
        },
        {
          legoItem: [
            {
              imgSrc: lego4,
              date: "10 / 07 / 2019",
              title: "ABC多元教育中心_A",
              text: "這位小朋友蠻聰明也很有想法，但就是比較愛吵鬧",
            },
            {
              imgSrc: lego5,
              date: "10 / 07 / 2019",
              title: "ABC多元教育中心_A",
              text: "可愛的2年級小朋友做的一台三輪車",
            },
            {
              imgSrc: lego6,
              date: "14 / 07 / 2019",
              title: "ABC多元教育中心_A",
              text: "再教投石器之前先做一個簡單的翹翹板~",
            },
          ],
        },
        {
          legoItem: [
            {
              imgSrc: lego7,
              date: "03 / 08 / 2019",
              title: "ABC多元教育中心_B",
              text: "裝有方向盤的四輪驅動車，小朋友都非常喜歡做車子呢。",
            },
            {
              imgSrc: lego8,
              date: "03 / 08 / 2019",
              title: "崇文國小-創意樂高",
              text: "伸縮夾課程!!小朋友學到了剛性與柔性結構也對連桿有基本認識。",
            },
            {
              imgSrc: lego9,
              date: "11 / 08 / 2019",
              title: "崇文國小-創意樂高",
              text: "一台很酷的風車，這堂課小朋友都特別聽話。",
            },
          ],
        },
      ],
    };
  },
};
</script>

<style lang="scss">
@import "../../assets/scss/variables.scss";
.swiper-lego {
  width: 73rem;
  // 三個卡片的容器
  .lego-slide {
    // 單一卡片
    .lego-card {
      width: 23rem;
      height: 29rem;
      border-radius: 0.625rem;
      border: 1px solid map-get($colors, "light-grey-2");
      overflow: hidden;
      transition: box-shadow 0.3s ease;

      &:hover {
        box-shadow: 2px 4px 15px 1.4px rgba(45, 45, 45, 0.13);
        border-color: transparent;
      }
      .lego-img {
        height: 72%;
      }
      .lego-date {
        margin-top: -1rem;
        border-radius: 0.4rem;
      }
    }
  }

  .lego-pagination {
    bottom: 0;
    // 底部三個點點
    .swiper-pagination-bullet {
      width: 2rem !important;
      height: 2rem !important;
      line-height: 2.1rem !important;
      text-align: center;
      margin: 0 0.625rem !important;
      background: #303036;
      text-align: center;
      opacity: 1;
      transition: background-color 0.3s ease;
      &:hover {
        background: map-get($colors, "primary");
      }
    }
    // 三個點點 被點擊後
    .swiper-pagination-bullet-active {
      background: map-get($colors, "primary");
      transition: background-color 0.3s ease;
    }
  }
}

@media all and (max-width: 1190px) {
  .swiper-lego {
    width: 65rem;
    .lego-slide {
      .lego-card {
        width: 20.5rem;
        height: 27.5rem;
      }
    }
  }
}

@media all and (max-width: 1080px) {
  .swiper-lego {
    width: 47rem;
    padding-bottom: 2.8rem !important;
    .lego-slide {
      .lego-card {
        width: 22rem;
        height: 28rem;
        margin-bottom: 0.5rem;
      }
    }
    .lego-pagination {
      bottom: 0;
    }
  }
}

@media all and (max-width: 800px) {
  .swiper-lego {
    width: 41rem;
    .lego-slide {
      .lego-card {
        width: 19.5rem;
        height: 25rem;
      }
    }
  }
}

@media all and (max-width: 680px) {
  .swiper-lego {
    width: 26rem;
    .lego-slide {
      .lego-card {
        width: 24rem;
        height: 29rem;
      }
    }
  }
}
</style>
