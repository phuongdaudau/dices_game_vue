<template>
	<div id="app">
		<div class="wrapper clearfix">
			<players 
				v-bind:isWinner="isWinner"
				v-bind:activePlayer="activePlayer"
				v-bind:scoresPlayer="scoresPlayer"
				v-bind:currentScore="currentScore"
			/>
            
            <controls 
				v-on:handleNewGame="handleNewGame"
				v-on:handleRollDice="handleRollDice"
				v-on:handleHoldScore="handleHoldScore"
				v-bind:finalScore="finalScore"
				v-on:handleChangeFinalScore="handleChangeFinalScore"
				v-bind:isPlaying="isPlaying"
			/>

			<dices 
				v-bind:dices="dices"
			/>

			<popup-rule 
				v-bind:isOpenPopup="isOpenPopup"
				v-on:handleConfirm="handleConfirm"
			/>

        </div>
	</div>
</template>

<script>
import Players from './components/Players.vue'
import Controls from './components/Controls.vue'
import Dices from './components/Dices.vue'
import PopupRule from './components/PopupRule.vue'

export default {
	name: 'app',
	data() {
		return {
			isPlaying: false,
			isOpenPopup: false,
			activePlayer: 1,
			dices: [5,5],
			scoresPlayer: [10,20],
			currentScore:30,
			finalScore:100
		}
	},
	components: {
		Players,
		Controls,
		Dices,
		PopupRule
	},
	computed:{
		isWinner(){
			let { scoresPlayer, finalScore } = this;
			if(scoresPlayer[0] >= finalScore || scoresPlayer[1] >= finalScore){
				this.isPlaying = false;
				return true;
			}
			return false;
		}
	},
	methods: {
		handleNewGame(){
			console.log('handle new game trong appvue');
			this.isOpenPopup = true;
		},
		handleConfirm(){
			this.isOpenPopup = false;
			this.isPlaying = true;
			this.activePlayer = 0;
			this.dices = [1,1];
			this.scoresPlayer = [0,0];
			this.currentScore = 0;
		},
		handleRollDice(){
			if(this.isPlaying){
				var dice1 = Math.floor(Math.random()*6) +1;
				var dice2 = Math.floor(Math.random()*6) +1;
				this.dices = [dice1, dice2];
				if(dice1 === 1 || dice2 === 1) {
                    let activePlayer = this.activePlayer;
                    setTimeout(function() {
                        alert(`Nguoi choi Player ${activePlayer + 1} đã quay trúng số 1. Rất tiếc`);
                    }, 10)
                    this.nextPlayer();
                } else {
                    this.currentScore = this.currentScore + dice1 + dice2;
                }

			}else{
				alert('Vui lòng nhấn nút New Game');
			}
		},
		nextPlayer(){
			this.activePlayer = this.activePlayer === 0 ? 1 : 0;
			this.currentScore = 0;
		},
		handleHoldScore(){
			if(this.isPlaying){
				// //c1 -this
				// this.scoresPlayer[this.activePlayer] = this.scoresPlayer[this.activePlayer] + this.currentScore;

				let { scoresPlayer, activePlayer, currentScore } = this;
				let oldScore = scoresPlayer[activePlayer];
				// // c2- clone data
				// let cloneScorePlayer = [...scoresPlayer];
				// 	cloneScorePlayer[activePlayer] = oldScore + currentScore;
				// this.scoresPlayer = cloneScorePlayer;

				//c3- $set
				this.$set(this.scoresPlayer, activePlayer, oldScore + currentScore);

				if(!this.isWinner){
					this.nextPlayer();
				}

			}else{
				alert('Vui lòng nhấn nút New Game');
			}
		},
		handleChangeFinalScore(e){
			var number = parseInt(e.target.value);
			if(isNaN(number)){
				this.finalScore = '';
			}else{
				this.finalScore = number;
			}
		
		}
		
	}
	
}
</script>

<style>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    
}

.clearfix::after {
    content: "";
    display: table;
    clear: both;
}

body {
    background-image: linear-gradient(rgba(62, 20, 20, 0.4), rgba(62, 20, 20, 0.4)), url(/public/assets/back.jpg);
    background-size: cover;
    background-position: center;
    font-family: Lato;
    font-weight: 300;
    position: relative;
    height: 100vh;
    color: #555;
}

.wrapper {
    width: 1000px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.3);
    overflow: hidden;
}
</style>
