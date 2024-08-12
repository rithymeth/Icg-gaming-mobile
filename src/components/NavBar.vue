<template>
  <nav
    class="bg-gray-900 text-white fixed top-0 left-0 right-0 z-50 shadow-md transition-colors duration-200"
    style="max-width: 420px; margin: 0 auto;"
  >
    <div class="max-w-full mx-auto px-4 flex justify-between h-16 items-center">
      <!-- Logo -->
      <div class="flex items-center">
        <button>
          <img class="h-8 w-auto" src="@/assets/logo.png" alt="Logo" to="/" />
        </button>
      </div>

      <!-- Mobile menu button -->
      <div class="flex items-center">
        <button
          @click="toggleMobileMenu"
          class="text-gray-400 hover:text-white focus:outline-none"
        >
          <i :class="[isMobileMenuOpen ? 'fas fa-times' : 'fas fa-bars']"></i>
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div v-if="isMobileMenuOpen" class="bg-gray-800">
      <router-link
        v-for="link in navLinks"
        :key="link.text"
        :to="link.route"
        class="block px-4 py-2 border-b border-gray-700 text-gray-400 hover:text-white"
        @click="toggleMobileMenu"
      >
        <i :class="[link.icon, 'mr-2']"></i>{{ link.text }}
      </router-link>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isMobileMenuOpen: false,
      navLinks: [
        { icon: "fas fa-home", text: "Home", route: "/" },
        { icon: "fas fa-futbol", text: "Sport", route: "/sport" },
        { icon: "fas fa-dice", text: "Casino", route: "/casino" },
        { icon: "fas fa-gamepad", text: "Slots", route: "/slots" },
        { icon: "fas fa-table", text: "Table Games", route: "/table-games" },
        { icon: "fas fa-rocket", text: "Crash Games", route: "/crash-games" },
        { icon: "fas fa-fish", text: "Fishing Games", route: "/fishing-games" },
        { icon: "fas fa-gamepad", text: "Arcade", route: "/arcade" },
        { icon: "fas fa-ticket-alt", text: "Lotto", route: "/lotto" },
        { icon: "fas fa-gift", text: "Promotions", route: "/promotions" },
        { icon: "fas fa-download", text: "Download", route: "/download" },
        { icon: "fas fa-handshake", text: "Affiliate", route: "/affiliate" },
        { icon: "fas fa-star", text: "Ambassador", route: "/ambassador" },
        { icon: "fas fa-question-circle", text: "Help", route: "/help" },
        { icon: "fas fa-phone", text: "Contact Us", route: "/contact-us" },
      ],
    };
  },
  methods: {
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
  },
};
</script>

<style scoped>
/* Navbar and Mobile Menu Styling */
</style>
