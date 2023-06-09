<template>
  <div class="logo-splasher" v-show="showSplashScreen">
    <div class="logo">
      <img src="https://i.postimg.cc/HxXX7ydh/Quicloc8-logo.png" class="content">
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      showSplashScreen: false,
    };
  },
  mounted() {
    // Show the splash screen after the page reloads
    this.showSplashScreen = true;
    // Start a timer to hide the splash screen after a certain duration
    setTimeout(() => {
      this.hideSplashScreen();
    }, 3500); // Adjust the duration as needed
  },
  methods: {
    hideSplashScreen() {
      this.showSplashScreen = false;
    },
  },
};
</script>
<style scoped>
.logo-splasher .logo {
  position: fixed;
  width: 100%;
  height: 100vh;
  opacity: 1;
  background: #8D8D95;
  animation: slide-in 3.5s; 
  z-index: 1000; 
}
.logo-splasher .content {
  --size: 300px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  animation: slide-in;
  animation-delay: 3.5s;
}
@keyframes slide-in {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    display: none;
  }
}
</style>