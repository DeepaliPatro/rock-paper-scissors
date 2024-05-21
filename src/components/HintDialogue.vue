<script>
    export default {
        data() {
            return {
                rules: [
                    "Rock beats Scissors",
                    "Scissors beats Paper",
                    "Paper beats Rock"
                ]
            };
        },
        methods: {
            closeDialogue() {
                this.$emit('close');
            }
        }
    };
</script>

<template>
    <div class="fixed inset-0 flex items-center justify-center bg-gray-900 bg-opacity-50">
      <div class="bg-white p-8 rounded-lg relative">
        <button @click="closeDialogue" class="absolute top-0 right-0 mt-2 mr-2 text-gray-500 hover:text-gray-700 focus:outline-none">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
        </button>
        <p class="text-lg text-left">Rules:</p>
        <ul class="list-disc mt-4 pl-8 text-left">
            <li v-for="(rule, index) in rules" :key="index" class="mb-2">{{ rule }}</li>
        </ul>
        <!-- <button @click="closeDialogue" class="mt-4 px-4 py-2 bg-blue-500 text-white rounded-md">Close</button> -->
      </div>
    </div>
</template>