<template>
  <ul class="collection-bar my-4 d-flex jc-center fl-wrap">
    <!-- bar item -->
    <li
      class="bar-item mx-3"
      :class="{
        'bar-item-active': active === index,
        'fs-lg': bars.length === 3,
      }"
      v-for="(item, index) in bars"
      :key="index"
      @click="changeCollectionContent(index)"
    >
      {{ item }}
    </li>
  </ul>
</template>

<script>
export default {
  props: ["bars"],
  data() {
    return {
      active: 0,
    };
  },
  methods: {
    changeCollectionContent(index) {
      if (this.active === index) {
        return;
      } //點擊同樣的直接return
      this.active = index; //看哪一個 baritem 要變藍色
      this.$emit("parentChangeContent", index);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables";

// bar 容器
.collection-bar {
  // bar 裡面的文字
  .bar-item {
    color: map-get($colors, "dark-grey");
    cursor: pointer;
    transition: color 0.3s ease;

    &:hover {
      color: map-get($colors, "primary");
    }
  }

  // bar item 被點擊後的樣式
  .bar-item-active {
    color: map-get($colors, "primary");
  }
}

@media all and (max-width: 800px) {
  // bar 裡面的文字
  .bar-item {
    margin: 0 0.8rem;
  }
}

@media all and (max-width: 680px) {
  // bar 裡面的文字
  .bar-item {
    margin: 0.2rem 0.7rem;
  }
}
</style>