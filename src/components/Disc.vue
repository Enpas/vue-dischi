<template>
  <div class="ep-disc-col col-sm-4 col-lg-2 ms-3">
    <img :src="disc.poster" :alt="disc.title">
    <h2>{{ disc.title }}</h2>
    <p>{{ disc.author }}</p>
    <p class="year">{{ disc.year }}</p>
  </div>
</template>

<script>
export default {
  name: 'Disc',
  props: {
    disc: Object
  }
}
</script>

<style lang="scss" scoped>
  @import '../assets/style/vars.scss';
  @import '../assets/style/general.scss';
  .ep-disc-col {
    min-height: 190px;
    background-color: $header-color;
    margin-bottom: 20px;
    padding: 20px;
    text-align: center;
    &:hover {
      transform: scale(1.03);
    }
    img {
      max-width: 100%;
      margin-bottom: 20px;
    }
  }
</style>