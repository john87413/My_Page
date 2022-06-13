<template>
  <!-- 最外容器 垂直排列 -->
  <div class="mx-5">
    <!-- 內容 容器 垂直排列 -->
    <div
      class="right-content my-4 py-1"
      v-for="(item, index) in intros"
      :key="index"
    >
      <p class="title text-primary fs-xxxl my-2 py-1 fw-bold">
        {{ item.count }}
      </p>
      <p class="text text-dark-grey fs-xlx my-2 py-1 fw-bold">
        {{ item.description }}
      </p>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      // 介紹內容
      intros: [
        { count: "2", description: "Аpps Developed" },
        { count: "3", description: "Web Developed" },
        { count: "1", description: "case" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@media all and (max-width: 1080px) {
  .right-content {
    text-align: center;
    .text {
      margin: 0.8rem 0rem;
    }
  }
}
</style>