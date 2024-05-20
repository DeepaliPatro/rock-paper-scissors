<script>
  export default {
    name: 'Scoreboard',
    props: {
      wins: {
        type: Number,
        required: true
      },
      draws: {
        type: Number,
        required: true
      },
      losses: {
        type: Number,
        required: true
      }
    }
  };
</script>

<template>
    <div class="mt-12 text-3xl mb-4">
        Wins({{ wins }}) | Draws({{ draws }}) | Losses({{ losses }})
    </div>
</template>