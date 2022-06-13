<template>
    <div id="lego" class="lego scroll-top py-1 my-2 pb-4">
        <myLegoTitle class="mb-3" :content="titleContent"></myLegoTitle>
        <!-- <myLegoBars :bars="barsContent"></myLegoBars> -->
        <legoSwiper></legoSwiper>
    </div>
</template>

<script>
import myLegoTitle from "../title/Title.vue";
// import myLegoBars from "../collection/CollectionBar.vue"
import legoSwiper from "./LegoSwiper.vue"

export default {
  components: {
    myLegoTitle,
    // myLegoBars,
    legoSwiper
  },
  data() {
    return {
      titleContent: {
        title: "Educate",
        text: "MORE PHOTO ABOUT",
      },
      barsContent: ["樂高-A", "樂高-B", "樂高-C"],
    };
  },
};
</script>

<style>
</style>