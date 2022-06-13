<template>
  <div id="about" class="scroll-top pt-4 pb-5">
    <!-- 關於我標題 -->
    <myAboutTitle v-bind:content="titleContent"></myAboutTitle>
    <!-- 關於我內容 -->
    <div class="d-flex jc-center fl-wrap mt-5">
      <aboutContent
        v-for="(item, index) in introContent"
        :key="index"
        v-bind:content="item"
      ></aboutContent>
    </div>
  </div>
</template>

<script>
import myAboutTitle from "../title/Title.vue";
import aboutContent from "./AboutContent.vue";

export default {
  components: {
    myAboutTitle,
    aboutContent,
  },
  data() {
    return {
      // 標題內容區
      titleContent: {
        title: "自我介紹",
        text: "WHO AM I",
      },
      // 關於我內容區
      introContent: [
        {
          title: "教育經驗",
          text: "擔任資管系學系服務學習助教，親自規劃與帶領課程，並且與麥米羅幼兒園合作進行不插電程式教育，以活潑有趣的方式讓學生了解<strong class='text-primary'>網頁UI排版</strong>和<strong class='text-primary'>電腦硬體的功用</strong>",
          icon: "book",
        },
        {
          title: "程式旅程",
          text: "在大學接觸程式開發時就被這廣闊無邊的領域吸引，總覺得程式可以做到任何事情，較熟悉的開發工具有<strong class='text-primary'>HTML、SCSS、Vue.js、Node.js、Express.js、MongoDB、JAVA</strong>",
          icon: "code",
        },
        {
          title: "網頁開發",
          text: "<a href='https://backsideadmin.herokuapp.com/' class='text-primary fw-bold'>後台管理平台</a>: 後端CRUD製作和前端串接API<br><a href='https://john87413.github.io/#/web' class='text-primary fw-bold'>履歷網站</a>:第一份專案,練習RWD<br><a href='/' class='text-primary fw-bold'>個人網站</a>: 主要為練習SEO優化<br>",
          icon: "web",
        },
      ],
    };
  },
};
</script>