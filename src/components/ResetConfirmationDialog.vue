<script>
  export default {
    methods: {
      confirm() {
        this.$emit('confirmed');
      },
      cancel() {
        this.$emit('canceled');
      }
    }
  };
</script>

<template>
    <div class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50">
      <div class="bg-white p-8 rounded-lg">
        <p class="text-lg">Are you sure you want to reset the score?</p>
        <div class="flex justify-center mt-4">
          <button @click="confirm" class="px-4 py-2 bg-blue-500 text-white rounded-md mr-4">Yes</button>
          <button @click="cancel" class="px-4 py-2 bg-gray-500 text-white rounded-md">No</button>
        </div>
      </div>
    </div>
</template>
  

  