<template>
  <div class="dashboard">
    <!-- Fixed sidebar with toggle button -->
    <div class="sidebar-toggle" :class="{ 'open': isSidebarOpen }" @click="toggleSidebar">
      <div class="menu-icon" :class="{ 'rotated': isSidebarOpen }">|||</div>
    </div>
    
    <!-- Sliding sidebar -->
    <div class="sidebar" :class="{ 'open': isSidebarOpen }">
      <div class="ctrl-btn">Ctrl+N</div>
    </div>
    
    <div class="main" :class="{ 'sidebar-open': isSidebarOpen }">
      <div class="header d-flex justify-between align-center mb-3">
        <h1>New chat!!!</h1>
        <div class="profile d-flex align-center">
          <div class="share-btn">Share</div>
        </div>
      </div>
      <div class="chat-box d-flex flex-column">
        <textarea v-model="codeInput" class="form-control flex-1" placeholder="Type your code here"></textarea>
        <div class="controls d-flex align-center">
          <div class="select-wrapper">
            <select v-model="selectedModel" class="form-control">
              <option value="">Claude 3 Opus</option>
              <option value="3d">Gemini 1.5 Pro</option>
              <option value="animation">DeepSeek-Coder 1.5</option>
            </select>
            <div class="select-icon">▼</div>
          </div>
          <button @click="attachFile" class="attach-btn ml-2">
            <div class="attach-icon">📎</div>
          </button>
          <button @click="submitCode" class="send-btn ml-2">
            <div class="send-icon">→</div>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainAppView',
  data() {
    return {
      codeInput: '',
      selectedModel: '',
      showSplashScreen: true,
      isSidebarOpen: false
    }
  },
  methods: {
    toggleSidebar() {
      this.isSidebarOpen = !this.isSidebarOpen;
    },
    submitCode() {
      if (!this.codeInput.trim()) {
        alert('Please enter some code first');
        return;
      }
      if (!this.selectedModel) {
        alert('Please select a model');
        return;
      }
      // Here you would process the code with the selected model
      console.log(`Processing code with ${this.selectedModel} model`);
      // The actual implementation would depend on your Electron backend
    },
    attachFile() {
      // Implement file attachment functionality
      console.log('Attaching file');
      // This would typically use Electron's dialog API
    },
    shareChat() {
      // Implement share functionality
      console.log('Sharing chat');
    }
  }
}
</script>

<style scoped>
/* Component specific styles that aren't covered by global CSS */
.dashboard {
  display: flex;
  height: 100vh;
  width: 100%;
  background-color: #d4d9cf;
  position: relative;
}

/* Sidebar toggle button fixed at the top-left corner */
.sidebar-toggle {
  position: fixed;
  top: 20px;
  left: 20px;
  width: 40px;
  height: 40px;
  background-color: #c6ccc0;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 100;
  transition: all 0.3s ease;
}

.sidebar-toggle.open {
  left: 60px;
}

.menu-icon {
  color: #000;
  font-size: 24px;
  transition: transform 0.3s ease;
}

.menu-icon.rotated {
  transform: rotate(90deg);
}

/* Sliding sidebar */
.sidebar {
  position: fixed;
  top: 0;
  left: -200px; /* Start hidden */
  width: 200px;
  border-radius: 10px;
  height: 100vh;
  /* background-color: #c6ccc0; */
  background-color: #afb4a9;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 80px;
  transition: left 0.3s ease;
  z-index: 90;
}

.sidebar.open {
  left: 0; /* Show when open */
}

.ctrl-btn {
  background-color: #e8ede3;
  color: #000;
  padding: 10px 8px;
  border-radius: 20px;
  font-family: 'Orbitron', sans-serif;
  font-size: 14px;
  margin-bottom: 40px;
  cursor: pointer;
}

/* Main content adjusts when sidebar is open */
.main {
  flex: 1;
  display: flex;
  flex-direction: column;
  padding: 20px 40px 20px 40px;
  margin-left: 0;
  transition: margin-left 0.3s ease;
}

.main.sidebar-open {
  margin-left: 80px;
}

h1 {
  font-family: 'Orbitron', sans-serif;
  color: #4a4a4a;
  font-size: 32px;
  font-weight: 500;
  margin-left: 40px; /* Space for menu icon */
}

.profile {
  display: flex;
  align-items: center;
}

.share-btn {
  font-family: 'Orbitron', sans-serif;
  color: #000;
  margin-right: 15px;
  cursor: pointer;
}

.chat-box {
  margin-top: 20px;
  flex: 1;
  background-color: #c1c7ba;
  border-radius: 8px;
  overflow: hidden;
}

textarea {
  background-color: #c1c7ba;
  border: none;
  padding: 20px;
  font-family: 'Orbitron', sans-serif;
  color: #4a4a4a;
  resize: none;
  font-size: 16px;
}

textarea::placeholder {
  color: #6b6b6b;
  font-family: 'Orbitron', sans-serif;
}

.controls {
  padding: 15px;
  background-color: #c1c7ba;
  border-top: 1px solid rgba(0,0,0,0.1);
}

.select-wrapper {
  position: relative;
  flex: 1;
}

select {
  background-color: #e8ede3;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  font-family: 'Orbitron', sans-serif;
  color: #4a4a4a;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding-right: 30px;
  cursor: pointer;
  width: 100%;
}

.select-icon {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 12px;
  pointer-events: none;
  color: #4a4a4a;
}

.attach-btn {
  background-color: #e8ede3;
  border: none;
  cursor: pointer;
  padding: 5px;
  border-radius: 50%;
  width: 38px;
  height: 38px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.attach-icon {
  font-size: 18px;
  color: #4a4a4a;
}

.send-btn {
  background-color: #e8ede3;
  border: none;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.send-icon {
  font-size: 22px;
  color: #4a4a4a;
}
</style>
