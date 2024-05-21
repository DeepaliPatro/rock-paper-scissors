<script>
  export default {
    props: {
      isOpen: {
        type: Boolean,
        required: true
      },
      menuItems: {
        type: Array,
        required: true
      },
      muted: {
        type: Boolean,
        default: false
      }
    },
    methods: {
      handleMenuItemClick(item) {
        if (!item.disabled) {
          this.$emit(item.action);
        }
        this.$emit('close');
      }
    }
  }
</script>
<template>
    <div v-if="isOpen" class="absolute left-4 top-4 bg-white shadow-lg rounded-lg min-w-max py-2 z-10">
        <a
        v-for="item in menuItems"
        :key="item.label"
        :href="item.disabled ? '#' : ''"
        :class="['block px-4 py-2 text-black', item.disabled ? 'cursor-not-allowed text-gray-300' : 'hover:bg-gray-100']"
        @click.prevent="handleMenuItemClick(item)"
        >
            {{ item.label === 'Mute' ? (muted ? 'Unmute' : 'Mute') : item.label }}
        </a>
    </div>
</template>