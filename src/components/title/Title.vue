<template>
  <div class="text-center">
    <div class="text-primary fs-xs my-3">{{ content.text }}</div>
    <h4 class="text-dark-grey fs-xxl fw-bold m-0">{{ content.title }}</h4>
  </div>
</template>

<script>
export default {
  props: ["content"],
};
</script>

<style>
</style>