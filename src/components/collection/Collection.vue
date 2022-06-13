<template>
  <div
    id="collection"
    class="scroll-top px-2 py-2 pb-4 bg-light-grey-1 d-flex flex-column ai-center"
  >
    <myCollectionTitle class="mb-4" :content="titleContent"></myCollectionTitle>
    <collectionBar :bars="barsContent" @parentChangeContent="triggerChangeContent"></collectionBar>
    <collectionContent ref="content"></collectionContent>
  </div>
</template>

<script>
import myCollectionTitle from "../title/Title.vue";
import collectionBar from "./CollectionBar.vue";
import collectionContent from "./CollectionContent.vue";

export default {
  components: {
    myCollectionTitle,
    collectionBar,
    collectionContent,
  },
  data() {
    return {
      titleContent: {
        title: "Side Projects",
        text: "MY WORKS",
      },
      barsContent: [
        "ALL",
        "MOBILE_APPS",
        "WEBPAGE",
        "STATIC_WEBPAGE",
        "APP_CASE",
      ],
    };
  },
  methods: {
    triggerChangeContent(index) {
      // 父组件通过$ref调用collectionContent中的事件方法
      this.$refs.content.changeDisplayContent(index);
    },
  },
};
</script>

<style>
</style>