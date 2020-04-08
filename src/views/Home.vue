<template>
  <div class="home">
    <van-button type="primary" @click="toAbout">主要按钮</van-button>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
  methods: {
    toAbout() {
      this.$router.push("/about");
    }
  }
};
</script>
