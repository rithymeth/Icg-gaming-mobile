<template>
  <div
    :class="['min-h-screen flex flex-col', isDarkMode ? 'dark' : '']"
    style="max-width: 420px; margin: 0 auto"
  >
    <div class="flex flex-1 flex-col">
      <!-- Main Content Area with Navbar -->
      <div class="flex-1 flex flex-col w-full">
        <NavBar :is-dark-mode="isDarkMode" @toggle-dark-mode="toggleDarkMode" />
        <main class="flex-grow p-4 transition-all duration-300">
          <!-- Main Content Goes Here -->
          <router-view />
        </main>
      </div>
    </div>
    <!-- Footer -->
    <!-- <FooterView class="flex-shrink-0" :is-dark-mode="isDarkMode" /> -->
  </div>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
// import FooterView from "@/components/FooterView.vue";

export default {
  components: {
    NavBar,
    // FooterView,
  },
  data() {
    return {
      isSidebarCollapsed: false,
      isDarkMode: false,
    };
  },
  methods: {
    toggleSidebar() {
      this.isSidebarCollapsed = !this.isSidebarCollapsed;
    },
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode;
      console.log("Dark mode toggled in App.vue. New state:", this.isDarkMode);
    },
  },
};
</script>

<style>
/* Global Styles */
html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
}

/* Dark Mode Styles */
.dark {
  background-color: #121212;
  color: #e0e0e0;
}

/* Ensure mobile-first layout */
.flex-1 {
  width: 100%;
  flex-direction: column;
}

/* Sidebar Styles */
.sidebar {
  width: 100%;
}

/* Navbar Styles */
.navbar {
  width: 100%;
}

/* Enforce mobile size layout */
.max-w-screen-mobile {
  max-width: 420px;
  margin: 0 auto;
}

/* Remove any large screen specific styles */
</style>
