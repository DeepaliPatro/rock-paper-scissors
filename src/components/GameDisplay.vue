<script>
    export default {
        name: 'GameDisplay',
        methods: {
            play(choice) {
                this.$emit('play', choice);
            },
        },
    };
</script>
<template>
    <div class="flex items-center justify-center gap-3 sm:gap-3 md:gap-5 mx-2 sm:mx-3 md:mx-5">
        <button @click="play('rock')" class="text-6xl sm:text-6xl lg:text-8xl rounded-full max-w-fit p-3 sm:p-4 lg:p-5 bg-white text-white shadow-lg shadow-slate-600 hover:bg-slate-200 hover:shadow-lg hover:shadow-slate-600 active:shadow-none transition-all duration-300">👊</button>
        <button @click="play('paper')" class="text-6xl sm:text-6xl lg:text-8xl rounded-full max-w-fit p-3 sm:p-4 lg:p-5 bg-white text-white shadow-lg shadow-slate-600 hover:bg-slate-200 hover:shadow-lg hover:shadow-slate-600 active:shadow-none transition-all duration-300">🫳</button>
        <button @click="play('scissors')" class="text-6xl sm:text-6xl lg:text-8xl rounded-full max-w-fit p-3 sm:p-4 lg:p-5 bg-white text-white shadow-lg shadow-slate-600 hover:bg-slate-200 hover:shadow-lg hover:shadow-slate-600 active:shadow-none transition-all duration-300">✌️</button>
    </div>
</template>