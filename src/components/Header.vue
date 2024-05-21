<script>
import HintDialogue from './HintDialogue.vue';
import MainMenu from './MainMenu.vue';

export default {
  components: {
    HintDialogue,
    MainMenu,
  },
  props: {
    confirmReset: {
      type: Function,
      required: true
    },
    muted: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      isDropdownOpen: false,
      title: 'Rock, Paper, Scissors',
      isHintOpen: false,
      menuItems: [
        { label: 'Profile', action: 'profile', disabled: true },
        { label: 'Mute', action: 'toggleMute', disabled: false },
        { label: 'Reset Score', action: 'handleReset', disabled: false },
        { label: 'Change Theme', action: 'changeTheme', disabled: true },
        { label: 'Statistics', action: 'viewStatistics', disabled: true },
        { label: 'About', action: 'about', disabled: true },
        { label: 'Feedback', action: 'feedback', disabled: true }
      ],
    };
  },
  methods: {
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen;
    },
    showHint() {
      this.isHintOpen = true;
    },
    closeHintDialogue() {
      this.isHintOpen = false;
    },
    toggleMute(){
      this.$emit('toggle-mute');
    },
    handleReset() {
      this.confirmReset();
    },
    profile() {
      // todo Add logic for profile
    },
    changeTheme() {
      // todo Add logic for changing theme
    },
    viewStatistics() {
      // todo Add logic to view statistics
    },
    about() {
      // todo Add logic to show about information
    },
    feedback() {
      // todo Add logic to show feedback form
    },
  },
}
</script>

<template>
  <nav class="bg-white shadow-md flex justify-between items-center mb-8 mt-8 pt-5">
    <!-- Left Section (Dropdown Button) -->
    <div class="ml-auto relative">
      <button @click="toggleDropdown" class="relative z-10">
        <svg v-if="!isDropdownOpen" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="3" stroke="currentColor" class="w-7 h-7 text-slate-500">
          <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="w-7 h-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
        </svg>
      </button>
      <!-- Dropdown Menu -->
      <MainMenu
        :isOpen="isDropdownOpen"
        :menuItems="menuItems"
        :muted="muted"
        @profile="profile"
        @toggleMute="toggleMute"
        @handleReset="handleReset"
        @changeTheme="changeTheme"
        @viewStatistics="viewStatistics"
        @about="about"
        @feedback="feedback"
        @close="toggleDropdown"
      />
    </div>
    
    <!-- Center Section (Header Title) -->
    <header class="container p-3 flex-grow flex justify-center">
      <h1 class="text-3xl sm:text-4xl md:text-5xl lg:text-5xl font-bold">{{ title }}</h1>
    </header>
    
    <!-- Right Section (Hint Button) -->
    <div class="mr-auto">
      <button @click="showHint" class="relative z-10">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-8 h-8">
          <path stroke-linecap="round" stroke-linejoin="round" d="m11.25 11.25.041-.02a.75.75 0 0 1 1.063.852l-.708 2.836a.75.75 0 0 0 1.063.853l.041-.021M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9-3.75h.008v.008H12V8.25Z" />
        </svg>
      </button>
    </div>
    <!-- Hint Dialogue -->
    <HintDialogue v-if="isHintOpen" @close="closeHintDialogue" />
  </nav>

</template>