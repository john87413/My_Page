<template>
  <!-- header -->
  <div class="my-header bg-white py-1 d-flex jc-center ai-center w-100">
    <!-- 選單按鈕 -->
    <i
      class="left-menu-icon iconfont icon-menu pl-4 fs-xl"
      @click="openLeft = openLeft === true ? false : true"
    ></i>
    <!-- Logo-->
    <a class="logo d-flex mr-4" title="SELF 個人網站">
      <img
        src="../../assets/images/self-logo-black.png"
        @click="scroll(5, `mySwiper`)"
      />
    </a>
    <!-- 選單 -->
    <ul class="nav-menu p-0 d-flex" :class="{ 'open-left': openLeft }">
      <li
        class="nav-menu-item mx-4"
        v-for="(item, index) in menus"
        :key="index"
        @click="
          index === 4 ? scrollToBottomest(index) : scroll(index, item.linkID)
        "
      >
        <a class="menu-link" :class="{ active: active === index }">{{
          item.title
        }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      active: 0, //被點擊的menu
      openLeft: false,
      moveBottomest: undefined,
      //網站nav 導航欄文字
      menus: [
        { title: "About me", linkID: "about" },
        { title: "Expertise", linkID: "expert" },
        { title: "Project", linkID: "collection" },
        { title: "Photo", linkID: "lego" },
        { title: "Contact me", linkID: "contact" },
      ],
    };
  },
  mounted() {
    // 監聽點擊螢幕事件
    document.addEventListener("click", (e) => {
      let flag = e.target.contains(
        document.getElementsByClassName("left-menu-icon")[0]
      );
      if (flag) {
        return;
      } else {
        this.openLeft = false;
      }
    });
  },
  methods: {
    // 滑到指定位置
    scroll(index, id) {
      this.active = index;
      let anchor = document.getElementById(id);
      anchor.scrollIntoView({ block: "start", behavior: "smooth" });
      this.openLeft = false;
    },
    // 計算是否到底
    scrollBottom() {
      let SH = document.body.scrollTop || document.documentElement.scrollTop;
      let CH =
        document.documentElement.clientHeight || document.body.clientHeight;
      let DH =
        document.documentElement.scrollHeight || document.body.scrollHeight;
      return SH + CH >= DH;
    },
    // 滑動到最底
    scrollToBottomest(index) {
      const scrollBottomest = () => {
        const scrollTop =
          document.documentElement.scrollTop || document.body.scrollTop;
        const distance = document.body.scrollHeight - scrollTop;
        if (!this.scrollBottom()) {
          this.moveBottomest = window.requestAnimationFrame(scrollBottomest);
          window.scrollTo(0, scrollTop + distance / 20);
        }
      };
      scrollBottomest();
      this.active = index;
      this.openLeft = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";
// 容器
.my-header {
  height: 4rem;
  z-index: 999;
  position: fixed;
  box-shadow: 1px 0.5px 8px rgba(20%, 20%, 40%, 0.5);
  //   左側選單按鈕
  .left-menu-icon {
    cursor: pointer;
    display: none;
  }
  // Logo
  .logo {
    img {
      cursor: pointer;
      width: 5.5rem;
    }
  }
  // 中間menu nav 選單
  .nav-menu {
    .menu-link {
      text-decoration: none;
    }
    .active {
      padding-bottom: 0.1rem;
      border-bottom: 3px solid map-get($colors, "light-grey");
      transition: all 0.3s ease;
    }
  }
}
@media all and (max-width: 900px) {
  // 容器
  .my-header {
    .left-menu-icon {
      display: block;
    }
    .logo {
      justify-content: center;
      width: 100%;
    }
    // 變成左側選單
    .nav-menu {
      position: absolute;
      top: 0;
      left: -20rem;
      flex-direction: column;
      width: 20rem;
      height: 100vh;
      margin-top: 4rem;
      background: map-get($colors, "white");
      border-top: 1px solid black;
      transition: left 0.3s ease;
      .nav-menu-item {
        margin: 0;
        padding: 1rem 1.5rem;
        transition: background-color 0.3s ease;
        &:hover {
          background: map-get($colors, "light-grey-1");
        }
        .active {
          padding-bottom: 0;
          border-bottom: none;
        }
      }
    }
    // 左側選單開關
    .open-left {
      left: 0;
    }
  }
}
</style>