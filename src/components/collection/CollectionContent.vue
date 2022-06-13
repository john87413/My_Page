<template>
  <!-- 展示作品集 -->
  <div
    class="collection-container d-flex fl-wrap jc-center"
    :style="containerChange"
  >
    <!-- 作品 item -->
    <div
      class="collection-content mx-3 my-2"
      ref="element"
      :class="{
        'display-content-change': arrDisplayNone.indexOf(index) > -1,
        'display-none': tempNone.indexOf(index) > -1,
      }"
      v-for="(item, index) in collectionLists"
      :key="index"
    >
      <!-- 作品 front 展示 -->
      <div class="content-front">
        <img class="front-img" :src="item.imgSrc" />
      </div>

      <!-- 作品 back 展示 -->
      <div
        class="content-back d-flex flex-column jc-center ai-center h-100 p-4"
      >
        <!-- 標題 -->
        <h5 class="back-title text-white fs-xl my-2 fw-bold">
          {{ item.title }}
        </h5>
        <!-- 文字 -->
        <p class="back-text text-white text-center my-2">{{ item.text }}</p>
        <!-- icon -->
        <i
          class="back-icon iconfont fs-lg text-primary bg-white p-1 text-center"
          :class="`icon-${item.icon}`"
          @click="showAlert(item.url)"
        ></i>
      </div>
    </div>
  </div>
</template>

<script>
import web_back from "../../assets/images/collection-web-back.png";
import web_static_1 from "../../assets/images/collection-web-static-1.png";
import web_static_2 from "../../assets/images/collection-web-static-2.png";
import app_main from "../../assets/images/collection-app-main.png";
import app_post from "../../assets/images/collection-app-post.png";
import app_relife from "../../assets/images/collection-app-relife.png";

export default {
  data() {
    return {
      // 作品集內容
      collectionLists: [
        {
          imgSrc: web_back,
          title: "後台管理平台",
          text: "前端使用了Vue + ElementUI，後端則是MongoDB + Express.js。",
          icon: "arrow-right",
          target: "QA & TESTING",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/2ea726",
        },
        {
          imgSrc: web_static_1,
          title: "履歷網站-1",
          text: "第一份side project，初次以Vue製作的RWD靜態網頁",
          icon: "arrow-right",
          target: "QA & TESTING",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/6880b4",
        },
        {
          imgSrc: web_static_2,
          title: "履歷網站-2",
          text: "第一份side project，圖片中的Swiper是當初自己手刻的",
          icon: "arrow-right",
          target: "CUSTOM SOFTWARE",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/6880b4",
        },
        {
          imgSrc: app_main,
          title: "長照資訊平台",
          text: "與中正大學高齡跨域創新研究中心合作的專案，協助中心製作一個東石在地資訊平台，讓長照人員可以快速了解當地資訊，並熟知照護者需求。",
          icon: "arrow-right",
          target: "MOBILE APPS",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/7fe53f",
        },
        {
          imgSrc: app_relife,
          title: "ReLife",
          text: "大三時與同學合作的專題成果，此專案是一個紀錄生活習慣的互動APP，希望能以APP中可愛的寵物吸引用戶養成良好生活習慣，而在這專案中我負責的是前端的畫面與功能製作",
          icon: "arrow-right",
          target: "QA & TESTING",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/relife-b994fb",
        },
        {
          imgSrc: app_post,
          title: "長照資訊平台",
          text: "當初與高齡跨域創新研究中心合作開發的資訊平台，這個貼文頁面當初與用戶花了蠻多時間討論與修改，而在這次的經驗中也學習到如何與用戶溝通和協調",
          icon: "arrow-right",
          target: "MOBILE APPS",
          isNone: false,
          url: "https://www.cakeresume.com/portfolios/7fe53f",
        },
      ],
      tempNone: [], // display : none
      arrDisplayNone: [], //scale要縮小的作品 index
      arrDisplay: [0, 1, 2, 3, 4, 5], //寬高不為零 會展示的作品 index
      displayContentHeight: 24.8,
      displayContentCount: 3,
    };
  },
  created() {
    this.handleResize();
  },
  mounted() {
    // 監聽網頁放大縮小
    window.addEventListener("resize", this.handleResize);
  },
  methods: {
    showAlert(url) {
      window.open(url, "_blank").focus();
    },
    // 用於計算容器高度
    handleResize() {
      if (window.innerWidth < 680) {
        this.displayContentHeight = 28;
        this.displayContentCount = 1;
      } else if (window.innerWidth < 800) {
        this.displayContentHeight = 24;
        this.displayContentCount = 2;
      } else if (window.innerWidth < 1080) {
        this.displayContentHeight = 26;
        this.displayContentCount = 2;
      } else {
        this.displayContentHeight = 24.8;
        this.displayContentCount = 3;
      }
    },
    // 變換要展示的作品數量
    changeDisplayContent(index) {
      //看是點擊到哪一個baritem
      switch (index) {
        case 0:
          this.displayAni([]);
          break;
        case 1:
          this.displayAni([0, 1, 2]);
          break;
        case 2:
          this.displayAni([3, 4, 5]);
          break;
        case 3:
          this.displayAni([0, 3, 4, 5]);
          break;
        case 4:
          this.displayAni([0, 1, 2, 4]);
          break;
      }
    },
    // 先讓全部display不為none 才能避免某些 item 沒有動畫
    delayTempNone() {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve("我是傳下去的值");
          this.tempNone = []; //先讓全部display 不為none
        }, 300);
      });
    },
    // 用來調用消失和出現動畫
    displayAni(displayNone) {
      this.arrDisplayNone = [0, 1, 2, 3, 4, 5]; //先把全部弄消失
      //取差集 把應該要出現的存入陣列 原本計算高度用
      this.arrDisplay = this.arrDisplayNone.filter(function (v) {
        return displayNone.indexOf(v) == -1;
      });
      this.delayTempNone().then(() => {
        // 有延遲才不會看不出動畫
        setTimeout(() => {
          this.arrDisplayNone = displayNone; //延遲秒後出現不再arrDisplayNone的index 作品
          this.tempNone = displayNone; //display: none 使用者才不會觸發hover效果
        }, 50);
      });
    },
  },
  computed: {
    containerChange() {
      return {
        height: `${
          Math.ceil(this.arrDisplay.length / this.displayContentCount) *
          (this.displayContentHeight + 1)
        }rem`, //動態計算容器高度(先計算有幾層在乘上一層的高度)
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables";

// 作品容器
.collection-container {
  width: 66rem;
  transition: width 200ms ease 0ms, height 200ms ease-in-out 0ms;
  // 作品卡片
  .collection-content {
    position: relative;
    transform: translate(0px, 0px) scale(1);
    transition: transform 300ms ease 0ms, opacity 400ms linear 0ms,
      width 300ms ease 0ms, height 300ms ease 0ms;

    // 作品 卡片 觸發旋轉
    &:hover {
      .content-front {
        transform: rotateY(180deg);
      }
      .content-back {
        z-index: 1;
        transform: rotateY(0deg);
        background: map-get($colors, "primary");
        opacity: 1;
      }
    }

    // 作品 卡片 前面
    .content-front {
      transition: transform 0.6s ease-in-out;
      .front-img {
        width: 20rem;
        height: 24.8rem;
        border-radius: 6%;
      }
    }

    // 作品 卡片 後面
    .content-back {
      position: absolute;
      left: 0;
      top: 0;
      opacity: 0;
      border-radius: 6%;
      z-index: -1;
      transform: rotateY(180deg);
      transition: all 0.6s ease-in-out;

      .back-icon {
        width: 2rem;
        height: 2rem;
        border-radius: 50%;
        transition: all 0.3s ease;

        &:hover {
          cursor: pointer;
          background: map-get($colors, "white-1");
        }
      }
    }
  }

  // 作品 Item 消失的動畫
  .display-content-change {
    transform: translate(0px, 0px) scale(0.01);
  }
  .display-none {
    display: none;
  }
}

@media all and (max-width: 1080px) {
  .collection-container {
    width: 46rem;
    .collection-content {
      .content-front {
        .front-img {
          width: 21rem;
          height: 26rem;
        }
      }
    }
  }
}

@media all and (max-width: 800px) {
  .collection-container {
    width: 40rem;
    .collection-content {
      margin: 0.3rem 0.5rem;
      .content-front {
        .front-img {
          width: 19rem;
          height: 24rem;
        }
      }
    }
  }
}

@media all and (max-width: 680px) {
  .collection-container {
    width: 25rem;
    .collection-content {
      width: 100%;
      .content-front {
        .front-img {
          width: 100%;
          height: 28rem;
        }
      }
      .content-back {
        .back-title {
          font-size: 1.8rem;
        }
        .back-text {
          font-size: 1.25rem;
        }
      }
    }
  }
}
</style>