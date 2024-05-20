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
    <div class="mt-12 text-2xl sm:text-2xl md:text-3xl lg:text-3xl  mb-4">
        Wins({{ wins }}) | Draws({{ draws }}) | Losses({{ losses }})
    </div>
</template>