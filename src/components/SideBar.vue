<template>
  <nav :class="[
    'fixed top-0 left-0 right-0 z-50 shadow-md transition-colors duration-200',
    isDarkMode ? 'bg-gray-900 text-white' : 'bg-white text-gray-800'
  ]">
    <div class="max-w-full mx-auto px-4">
      <div class="flex justify-between h-16">
        <!-- Logo -->
        <div class="flex items-center">
          <img class="h-8 w-auto" :src="isDarkMode ? require('@/assets/logo.png') : require('@/assets/logo1.png')" alt="Casino Logo">
        </div>

        <!-- Mobile menu button -->
        <div class="flex items-center">
          <button @click="toggleMobileMenu" :class="[
            'inline-flex items-center justify-center p-2 rounded-md focus:outline-none focus:ring-2 focus:ring-inset focus:ring-blue-500',
            isDarkMode
              ? 'text-gray-400 hover:text-white hover:bg-gray-700'
              : 'text-gray-400 hover:text-gray-500 hover:bg-gray-100'
          ]">
            <span class="sr-only">Open main menu</span>
            <i :class="[isMobileMenuOpen ? 'fas fa-times' : 'fas fa-bars', 'block h-6 w-6']"></i>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile menu -->
    <div v-if="isMobileMenuOpen" :class="['sm:hidden', isDarkMode ? 'bg-gray-900' : 'bg-white']">
      <div class="pt-2 pb-3 space-y-1">
        <router-link v-for="link in navLinks" :key="link.text" :to="link.route"
           :class="[
             'flex items-center pl-3 pr-4 py-2 border-l-4 text-base font-medium',
             isDarkMode
               ? 'text-gray-300 hover:bg-gray-700 hover:text-white'
               : 'text-gray-500 hover:bg-gray-50 hover:text-gray-700',
             'border-transparent'
           ]">
          <i :class="link.icon + ' mr-3'"></i>
          {{ link.text }}
        </router-link>
      </div>
      <div :class="['pt-4 pb-3 border-t', isDarkMode ? 'border-gray-700' : 'border-gray-200']">
        <div v-if="isLoggedIn" class="flex items-center px-4">
          <div class="flex-shrink-0">
            <img class="h-10 w-10 rounded-full" src="@/assets/224.png" alt="User avatar">
          </div>
          <div class="ml-3">
            <div :class="['text-base font-medium', isDarkMode ? 'text-white' : 'text-gray-800']">{{ userName }}</div>
            <div :class="['text-sm font-medium', isDarkMode ? 'text-gray-400' : 'text-gray-500']">{{ userEmail }}</div>
          </div>
        </div>
        <div class="mt-3 space-y-1">
          <router-link v-if="isLoggedIn" to="/profile" :class="[
            'block px-4 py-2 text-base font-medium',
            isDarkMode ? 'text-gray-300 hover:bg-gray-700 hover:text-white' : 'text-gray-500 hover:bg-gray-100 hover:text-gray-800'
          ]">Your Profile</router-link>
          <router-link v-if="isLoggedIn" to="/settings" :class="[
            'block px-4 py-2 text-base font-medium',
            isDarkMode ? 'text-gray-300 hover:bg-gray-700 hover:text-white' : 'text-gray-500 hover:bg-gray-100 hover:text-gray-800'
          ]">Settings</router-link>
          <a v-if="isLoggedIn" @click="logout" :class="[
            'block px-4 py-2 text-base font-medium cursor-pointer',
            isDarkMode ? 'text-gray-300 hover:bg-gray-700 hover:text-white' : 'text-gray-500 hover:bg-gray-100 hover:text-gray-800'
          ]">Sign out</a>
          <router-link v-else to="/auth" :class="[
            'block px-4 py-2 text-base font-medium',
            isDarkMode ? 'text-gray-300 hover:bg-gray-700 hover:text-white' : 'text-gray-500 hover:bg-gray-100 hover:text-gray-800'
          ]">
            Login / Register
          </router-link>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  props: {
    isDarkMode: Boolean,
  },
  data() {
    return {
      isLoggedIn: false, // This should be reactive based on your auth state
      userName: 'John Doe', // This should be set when user logs in
      userEmail: 'john@example.com', // This should be set when user logs in
      isMobileMenuOpen: false,
      navLinks: [
        { icon: 'fas fa-home', text: 'Home', route: '/' },
        { icon: 'fas fa-futbol', text: 'Sport', route: '/sport' },
        { icon: 'fas fa-dice', text: 'Casino', route: '/casino' },
        { icon: 'fas fa-slot-machine', text: 'Slots', route: '/slots' },
        { icon: 'fas fa-table', text: 'Table Games', route: '/table-games' },
        { icon: 'fas fa-rocket', text: 'Crash Games', route: '/crash-games' },
        { icon: 'fas fa-fish', text: 'Fishing Games', route: '/fishing-games' },
        { icon: 'fas fa-gamepad', text: 'Arcade', route: '/arcade' },
        { icon: 'fas fa-ticket-alt', text: 'Lotto', route: '/lotto' },
        { icon: 'fas fa-gift', text: 'Promotions', route: '/promotions' },
        { icon: 'fas fa-download', text: 'Download', route: '/download' },
        { icon: 'fas fa-handshake', text: 'Affiliate', route: '/affiliate' },
        { icon: 'fas fa-star', text: 'Ambassador', route: '/ambassador' },
        { icon: 'fas fa-question-circle', text: 'Help', route: '/help' },
        { icon: 'fas fa-phone', text: 'Contact Us', route: '/contact-us' },
      ],
    };
  },
  methods: {
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
    logout() {
      // Implement logout logic here
      this.isLoggedIn = false;
      // You might want to redirect to the home page or login page after logout
    },
  },
};
</script>

<style scoped>
/* Mobile-specific Styles */
</style>
