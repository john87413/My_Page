<template>
  <div class="experience d-flex ai-center jc-center">
    <left-circle></left-circle>
    <right-intro></right-intro>
  </div>
</template>

<script>
import leftCircle from "./LeftCircle.vue";
import rightIntro from "./RightContent.vue";

export default {
  components: {
    "left-circle": leftCircle,
    "right-intro": rightIntro,
  },
};
</script>

<style lang="scss" scoped>
@media screen and (max-width: 1080px) {
  .experience {
    flex-direction: column;
  }
}
</style>