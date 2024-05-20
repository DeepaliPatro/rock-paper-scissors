<script>
    export default {
        name: 'ResultsDisplay',
        props: {
            choice: {
            type: String,
            required: true
            },
            computerChoice: {
            type: String,
            required: true
            },
            message: {
            type: String,
            required: true
            }
        },
        computed: {
            playerResultClass() {
                return this.message === 'You Win 🙂' ? 'bg-green-600' : this.message === "It's a draw 😐" ? 'bg-slate-600' : 'bg-red-600';
            },
            computerResultClass() {
                return this.message === 'You Win 🙂' ? 'bg-red-600' : this.message === "It's a draw 😐" ? 'bg-slate-600' : 'bg-green-600';
            }
        },
        methods: {
            getEmoji(choice) {
                if (choice === 'rock') {
                    return '👊';
                } else if (choice === 'paper') {
                    return '🫳';
                } else if (choice === 'scissors') {
                    return '✌️';
                } else {
                    return ''; // Return empty string if choice is invalid
                }
            },
        }
    };
</script>

<template>
    <div>
        <div class="flex items-center justify-center gap-10 mx-5">
            <div class="flex flex-col items-center">
                <p class="text-3xl mb-4">You choose</p>
                <div :class="['text-9xl rounded-full text-white p-5 max-w-fit', playerResultClass]">
                    {{ getEmoji(choice) }}
                </div>
            </div>
    
            <div class="-rotate-45"><span class="text-3xl mb-4">Vs</span></div>
    
            <div class="flex flex-col items-center">
                <p class="text-3xl mb-4">Computer choose</p>
                <div :class="['text-9xl rounded-full text-white p-5 max-w-fit', computerResultClass]">
                    {{ getEmoji(computerChoice) }}
                </div>
            </div>
        </div>
        <div class="text-4xl p-6">
          {{ message }}
        </div>
    </div>
</template>