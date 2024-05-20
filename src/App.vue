<script>
  import Header from './components/Header.vue';
  import GameDisplay from './components/GameDisplay.vue';
  import ResultsDisplay from './components/ResultsDisplay.vue';
  import Scoreboard from './components/Scoreboard.vue';

  export default {
    components: {
      Header,
      GameDisplay,
      ResultsDisplay,
      Scoreboard,
    },
    data: function(){
      return {
        wins: parseInt(localStorage.getItem('wins')) || 0,
        draws: parseInt(localStorage.getItem('draws')) || 0,
        losses: parseInt(localStorage.getItem('losses')) || 0,

        choice: null,
        computerChoice: null,
        message: '',
        result: null,

        results : {
          'rock': {
            'rock': 'draw',
            'paper': 'loss',
            'scissors': 'win'
          },
          'paper': {
            'rock': 'win',
            'paper': 'draw',
            'scissors': 'loss'
          },
          'scissors': {
            'rock': 'loss',
            'paper': 'win',
            'scissors': 'draw'
          }
        }
      }
    },
    
    methods: {
      play(choice){
        this.choice = choice;
        this.computerChoice = this.getComputerChoice();
        this.message = this.getResultMessage();
        this.updateScore(this.result);
      },

      getComputerChoice() {
        const choices = ['rock', 'paper', 'scissors'];
        return choices[Math.floor(Math.random() * choices.length)];
      },

      getResultMessage() {
        this.result = this.results[this.choice][this.computerChoice];
        if (this.result === 'win') {
          return 'You Win 🙂';
        } else if (this.result === 'draw') {
          return "It's a draw 😐";
        } else if(this.result === 'loss'){
          return 'You lose ☹️';
        }
      },

      updateScore(result) {
        if (result === 'win') {
          this.wins++;
          localStorage.setItem('wins', this.wins);
        } else if (result === "draw") {
          this.draws++;
          localStorage.setItem('draws', this.draws);
        } else if(result === 'loss'){
          this.losses++;
          localStorage.setItem('losses', this.losses);
        }
      },
      playAgain(){
        this.choice = null;
        this.computerChoice = null;
        this.message = '';
        this.result = null;
      },
      resetScore(){
        this.wins = 0;
        this.draws = 0;
        this.losses = 0;
        localStorage.setItem('wins', this.wins);
        localStorage.setItem('draws', this.draws);
        localStorage.setItem('losses', this.losses);
        this.playAgain();
      },
      confirmReset() {
        if (window.confirm('Are you sure you want to reset the score?')) {
          this.resetScore();
        }
      },
    }
  };
</script>

<template>
  <div class="bg-white text-slate-500 text-center min-h-screen flex flex-col">
    <Header />
    <main class="container">
      <div v-if="choice == null" class="flex items-center justify-center gap-5 mx-5">
        <GameDisplay @play="play" />
      </div>
      <div v-else>
        <ResultsDisplay :choice="choice" :computerChoice="computerChoice" :message="message" />
        <div class="flex items-center justify-center gap-5 mx-5">
          <button @click="playAgain()" class="text-lg rounded-full w-50 p-5 bg-white text-slate-500 shadow-lg shadow-slate-600 hover:bg-slate-200 hover:shadow-lg hover:shadow-slate-600 active:shadow-none transition-all duration-300 py-2 px-4">
            Play Again
          </button>
          <button @click="confirmReset" class="text-lg rounded-full w-50 p-5 bg-white text-slate-500 shadow-lg shadow-slate-600 hover:bg-slate-200 hover:shadow-lg hover:shadow-slate-600 active:shadow-none transition-all duration-300 py-2 px-4">
            Reset score
          </button>
        </div>
        <Scoreboard :wins="wins" :draws="draws" :losses="losses" />
      </div>
    </main>
  </div>
</template>
