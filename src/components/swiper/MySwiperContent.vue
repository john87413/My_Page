<template>
  <div class="swiper-content">
    <!-- title text -->
    <h2 class="title fs-xxl text-dark-grey">
      {{ sigleContent.title }}<br />
      {{ sigleContent.subTitle }}
    </h2>
    <!-- content text -->
    <p class="fs-lg my-3 text-light-grey">{{ sigleContent.text }}</p>
    <!-- button -->
    <button class="bt-back-1 bt-nav-1 ripple mr-3 py-2" @click="showAlert">
      Learn More
    </button>
    <button class="bt-back-2 bt-nav-2 ripple py-2" @click="showAlert">Get in Touch</button>
  </div>
</template>

<script>
export default {
  props: ["sigleContent"],
  methods: {
    showAlert() {
      window.open("https://www.cakeresume.com/johnnew", '_blank').focus();
    },
  },
};
</script>

<style lang="scss" scoped>
.swiper-content {
  margin-right: 25%;
  width: 22rem;
  z-index: 1;
  .title {
    line-height: 3rem;
  }
}
@media all and (max-width: 500px) {
  .swiper-content {
    margin-right: 0;
  }
}
</style>