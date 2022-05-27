<template>
  <div class="wrapper-control">
    <button 
        v-on:click="newGame"
        class="control btn-new"><i class="ion-ios-plus-outline"></i>New game</button>
    <button 
        v-on:click="rollDice"
        class="control btn-roll"><i class="ion-ios-loop"></i>Roll dice</button>
    <button 
        v-on:click="handleHoldScore"
        class="control btn-hold"><i class="ion-ios-download-outline"></i>Hold</button>
    
    <input 
        v-bind:disabled="isPlaying"
        v-bind:value="finalScore"
        v-on:input="$emit('handleChangeFinalScore', $event)"
        type="number" placeholder="Final score" class="final-score">
  </div>
</template>

<script>
export default {
    name: 'controls',
    data(){
        return {

        }
    },
    props: {
        finalScore: { type: [Number, String ], default: 100},
        isPlaying: { type: Boolean, default: false}
    },
    methods: {
        newGame(){
            console.log('new game trong control.Vue');
            this.$emit('handleNewGame');
        },
        rollDice(){
            this.$emit('handleRollDice');
        }, 
        handleHoldScore(){
            this.$emit('handleHoldScore');
        }
    }

}
</script>

<style>


</style>