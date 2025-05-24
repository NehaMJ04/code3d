<template>
  <div class="splash-screen fade-in">
    <div class="login-link">Login</div>
    
    <div class="content d-flex flex-column align-center ">
      <div class="logo-container">
        <img src="/src/assets/Logo.png" alt="CODE3D Logo" class="logo">
      </div>
      
      <div class="tagline">
        "Ctrl+shift+reality"
      </div>
      
      <button class="try-button slide-in-bottom" @click="goToMainApp">
        TRY IT FOR FREE
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  mounted() {
    // No longer using automatic timeout
  },
  methods: {
    goToMainApp() {
      // Emit event to trigger transition to main app view
      this.$emit('splashComplete');
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700;800;900&display=swap');

.splash-screen {
  height: 100vh;
  width: 100%;
  position: relative;
  background-color: rgba(107, 112, 92, 0.8);
  background-image: repeating-linear-gradient(
    90deg,
    rgba(0, 0, 0, 0.1),
    rgba(0, 0, 0, 0.1) 1px,
    transparent 1px,
    transparent 20px
  );
  overflow: hidden;
  font-family: 'Orbitron', sans-serif;
}

/* Fade in animation */
.fade-in {
  animation: fadeIn 1.5s ease-in;
  opacity: 1;
}

@keyframes fadeIn {
  0% { opacity: 0; }
  100% { opacity: 1; }
}

/* Slide-in animations */
/* .slide-in-left {
  animation: slideInLeft 1.2s ease-out 0.5s both;
} */

/* .slide-in-right {
  animation: slideInRight 1.2s ease-out 0.8s both;
} */

.slide-in-bottom {
  animation: slideInBottom 1.2s ease-out 0.5s both;
}

/* .slide-in-top {
  animation: slideInTop 1.2s ease-out 1.4s both;
} */
/* 
@keyframes slideInLeft {
  0% {
    transform: translateX(-100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
} */

/* @keyframes slideInRight {
  0% {
    transform: translateX(100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
} */

@keyframes slideInBottom {
  0% {
    transform: translateY(100px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
}

/* @keyframes slideInTop {
  0% {
    transform: translateY(-50px);
    opacity: 0;
  }
  100% {
    transform: translateY(0);
    opacity: 1;
  }
} */

.login-link {
  /* position: absolute;
  top: 30px;
  right: 40px;
  color: #000;
  font-size: 1.2rem;
  font-family: 'Orbitron', sans-serif;
  cursor: pointer; */

  right: 40px;
  color: #000;
  font-size: 1.2rem;
  font-family: 'Orbitron', sans-serif;
  cursor: pointer;
  width: 100%;
  height: 70px;
  background: #797d6eb0;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 100;
  display: flex;
  align-content: space-around;
  align-items: center;
  justify-content: flex-end;
  padding: 10px 20px;
}

.content {
  height: 100%;
  width: 100%;
  padding: 20px;
  display: flex;
  justify-content: center;
}

.logo-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.logo {
  width: 250px;
  margin-bottom: 0;
}

h1 {
  font-size: 3.5rem;
  color: #000;
  font-family: 'Orbitron', sans-serif;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-top: 0;
}

.tagline {
  font-size: 20px;
  color:#e4e4e4;
  font-family: 'Orbitron', sans-serif;
  margin-bottom: 40px;
}

.try-button {
  background-color: #000;
    color: white;
    border: none;
    padding: 15px 40px;
    font-size: 12px;
    cursor: pointer;
    text-transform: uppercase;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    font-family: 'Orbitron', sans-serif;
}

.try-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  background: #222;

}
</style>
