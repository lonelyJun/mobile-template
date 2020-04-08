<template>
  <div id="app">
    <transition :name="transitionName">
      <keep-alive>
        <router-view></router-view>
      </keep-alive>
    </transition>
  </div>
</template>

<script>
export default {
  name: "app",
  watch: {
    $route() {
      let isBack = this.$router.isBack; //监听是后退还是跳转
      if (isBack) {
        this.transitionName = "slide-left";
      } else {
        this.transitionName = "slide-right";
      }
      this.$router.isBack = false;
    }
  },
  data() {
    return {
      transitionName: "slide-right"
    };
  },
  mounted() {
    window.addEventListener("popstate", () => {
      this.$router.isBack = true;
    });
  },
  components: {}
};
</script>

<style lang="scss">
html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  width: 100%;
  height: 100%;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  .slide-left-enter,
  .slide-right-leave-to {
    opacity: 0;
    transform: translateX(100%);
  }

  .slide-left-leave-to,
  .slide-right-enter {
    opacity: 0;
    transform: translateX(-100%);
  }

  .slide-left-enter-active,
  .slide-left-leave-active,
  .slide-right-enter-active,
  .slide-right-leave-active {
    transition: 1s;
    position: absolute;
    top: 0;
  }
}
</style>
