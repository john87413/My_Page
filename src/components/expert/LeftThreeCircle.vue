<template>
  <!-- 三圓形容器 -->
  <div class="circle-container d-flex flex-column ai-end">
    <!-- 三圓形 -->
    <div
      class="circle-item bg-primary d-flex flex-column ai-center jc-center"
      :class="{ 'circle-item-active': active === index }"
      v-for="(item, index) in circleIcons"
      :key="index"
      @click="changeExpertiseSlide(index)"
    >
      <!-- 圓形icon -->
      <i
        :class="`circle-icon iconfont text-white icon-${item.icon} pb-3`"
      ></i>
      <p class="circle-text fs-l text-white">click</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 左邊三圓圈資料
      circleIcons: [{ icon: "book" }, { icon: "web" }, { icon: "APP" }],
      //被點擊或hover的圓圈
      active: 1,
    };
  },
  methods: {
    changeExpertiseSlide(index) {
      this.active = index;
      this.$emit("parentChangeSlide", index); //監聽從父組件調用兄弟組件的方法
    },
    //給兄弟組件做監聽
    changeCircle(index) {
      this.active = index;
    },
  },
};
</script>

<style scoped lang="scss">
@import "../../assets/scss/variables.scss";
// 三圓形
.circle-item {
  position: relative;
  border-radius: 50%;
  width: 9rem;
  height: 9rem;
  cursor: pointer;

  // 第一個
  &:nth-child(1) {
    margin-right: 2rem;
  }
  // 第二個
  &:nth-child(2) {
    margin-right: 11.5rem;
    margin-top: -2.5rem;
    margin-bottom: -3rem;
    width: 14rem;
    height: 14rem;
    // 裡面icon
    .circle-icon {
      font-size: 8rem;
      font-weight: 500;
    }
  }
  // 外圍藍色圓圈
  &::before {
    content: "";
    position: absolute;
    top: 0px;
    left: 0px;
    right: 0px;
    bottom: 0px;
    border: 0.25rem solid map-get($colors, "light-blue");
    opacity: 0;
    border-radius: 50%;
    transition: all 0.3s;
  }
  // 觸發後 外圍圓圈出現
  &:hover::before {
    top: -0.5rem;
    left: -0.5rem;
    right: -0.5rem;
    bottom: -0.5rem;
    opacity: 1;
  }

  // 圓形內icon
  .circle-icon {
    font-size: 5rem;
  }

  .circle-text{
    position: absolute;
    bottom: 0.7rem;
  }
}
// 點擊外圍圓圈也要出現
.circle-item-active::before {
  top: -0.5rem;
  left: -0.5rem;
  right: -0.5rem;
  bottom: -0.5rem;
  opacity: 1;
}
@media all and (max-width: 1080px) {
  // 容器 變水平排列
  .circle-container {
    flex-direction: row;
    // 圓形調大小
    .circle-item {
      width: 11rem;
      height: 11rem;
      margin: 0 1.5rem;
      // 圓形內icon調大小
      .circle-icon {
        font-size: 6.5rem;
      }
    }
  }
}
@media all and (max-width: 800px) {
  .circle-container {
    // 圓形調大小
    .circle-item {
      width: 9.5rem;
      height: 9.5rem;
      margin: 0 1rem;
      // 圓形內icon調大小
      .circle-icon {
        font-size: 5rem;
      }
    }
  }
}
@media all and (max-width: 590px) {
  .circle-container {
    // 圓形調大小
    .circle-item {
      width: 7.5rem;
      height: 7.5rem;
      // 圓形內icon調大小
      .circle-icon {
        font-size: 3.5rem;
      }
    }
  }
}
@media all and (max-width: 400px) {
  .circle-container {
    // 圓形調大小
    .circle-item {
      width: 7rem;
      height: 7rem;
      margin: 0 0.6rem;
      &::before {
        border: 0.2rem solid map-get($colors, "light-blue");
      }
      // 觸發後 外圍圓圈出現
      &:hover::before {
        top: -0.3rem;
        left: -0.3rem;
        right: -0.3rem;
        bottom: -0.3rem;
      }
      // 圓形內icon調大小
      .circle-icon {
        font-size: 3.5rem;
      }
    }
  }
  // 圓外 圓框框
  .circle-item-active::before {
    top: -0.3rem;
    left: -0.3rem;
    right: -0.3rem;
    bottom: -0.3rem;
  }
}
</style>