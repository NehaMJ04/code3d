<template>
  <div class="main-container">
    <transition name="quick-fade" mode="out-in">
      <App v-if="showSplash" @splashComplete="handleSplashComplete" />
      <MainAppView v-else />
    </transition>
  </div>
</template>

<script>
import App from './App.vue';
import MainAppView from './main-app-view.vue';

export default {
  name: 'MainContainer',
  components: {
    App,
    MainAppView
  },
  data() {
    return {
      showSplash: true
    }
  },
  methods: {
    handleSplashComplete() {
      // Immediately transition to main app with no delay
      this.showSplash = false;
    }
  }
}
</script>

<style scoped>
.main-container {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  position: relative;
}

/* Quick transition effects */
.quick-fade-enter-active,
.quick-fade-leave-active {
  transition: opacity 0.1s ease;
}

.quick-fade-enter-from,
.quick-fade-leave-to {
  opacity: 0;
}
</style> 