<template>
  <div class="about" @click="toHome">
    <van-button type="primary">back</van-button>
    <h1>This is an about page</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },

  components: {},

  computed: {},

  methods: {
    toHome() {
      this.$router.back();
    }
  }
};
</script>
<style lang='scss' scoped>
</style>
