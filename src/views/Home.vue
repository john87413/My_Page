<template>
  <main class="main-view bg-white">
    <myHeader></myHeader>
    <bannerSwiper></bannerSwiper>
    <about></about>
    <experience></experience>
    <autobiography></autobiography>
    <expertise></expertise>
    <collection></collection>
    <lego></lego>
    <myFooter></myFooter>
  </main>
</template>

<script>
import myHeader from '../components/header/Header.vue'
import bannerSwiper from "../components/swiper/MySwiper.vue";
import about from "../components/about/About.vue";
import experience from "../components/experience/Experience.vue";
import autobiography from "../components/autobiography/Autobiography.vue";
import expertise from "../components/expert/Expertise.vue";
import collection from "../components/collection/Collection.vue";
import lego from "../components/lego/Lego.vue";
import myFooter from "../components/footer/Footer.vue";

export default {
  components: {
    myHeader,
    bannerSwiper,
    about,
    experience,
    autobiography,
    expertise,
    collection,
    lego,
    myFooter,
  },
};
</script>

<style scoped lang="scss">
// 用來避免看不到footer
.main-view {
  margin-bottom: 33.5rem;
}
// 取消footer的隱藏
@media all and (max-width: 900px) {
  .main-view {
    margin-bottom: 0rem;
  }
}
</style>
