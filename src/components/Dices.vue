<template>
  <div class="wrapper-dices">
      
        <div id="dice-1" class="dice">
            <div class="spinner " v-bind:class="'dice-' + dices[0]" >
                <div class="face1">1</div>
                <div class="face2">2</div>
                <div class="face3">3</div>
                <div class="face4">4</div>
                <div class="face5">5</div>
                <div class="face6">6</div>
            </div>
        </div>
        <div id="dice-2" class="dice">
            <div class="spinner" v-bind:class="'dice-' + dices[1]">
                <div class="face1">1</div>
                <div class="face2">2</div>
                <div class="face3">3</div>
                <div class="face4">4</div>
                <div class="face5">5</div>
                <div class="face6">6</div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
    name: 'dices', 
    data(){
        return {
        
        }
    },
    props: {
        dices: {type: Array, default: [2,2] }
    }

}
</script>

<style>
/**********************************************
*** Control
**********************************************/
.control {
    position: absolute;
    width: 200px;
    left: 50%;
    transform: translateX(-50%);
    color: #555;
    background: none;
    border: none;
    font-family: Lato;
    font-size: 20px;
    text-transform: uppercase;
    cursor: pointer;
    font-weight: 300;
    transition: background-color 0.3s, color 0.3s;
}
.control.disable {
    pointer-events: none;
}

.control:hover { font-weight: 600; }
.control:hover i { margin-right: 20px; }

.control:focus {
    outline: none;
}

.control i {
    color: #42b983;
    display: inline-block;
    margin-right: 15px;
    font-size: 32px;
    line-height: 1;
    vertical-align: text-top;
    margin-top: -4px;
    transition: margin 0.3s;
}

.btn-new { top: 45px;}
.btn-roll { top: 403px;}
.btn-hold { top: 467px;}

.final-score {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 520px;
    color: #555;
    font-size: 18px;
    font-family: 'Lato';
    text-align: center;
    padding: 10px;
    width: 160px;
    text-transform: uppercase;
}

.final-score:focus { outline: none; }


#dice-1 { top: 120px; }
#dice-2 { top: 250px; }

.dice {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 120px;
    height: 120px;
    box-shadow: 0px 10px 60px rgba(0, 0, 0, 0.10);
}
.spinner div {
    position: absolute;
    width: 120px;
    height: 120px;
    border: 1px solid #ccc;
    box-shadow: 0 0 20px rgba(0,0,0,0.2);
    text-align: center;
    line-height: 120px;
    font-size: 100px;
    color: #42b983;
    font-size: 0;
    transition: all .3s ease;
    opacity: 1;
}

.spinner .face1 { 
    -webkit-transform: translateZ(60px);
    -ms-transform: translateZ(60px);
    transform: translateZ(60px);
    background-image: url("/public/assets/dice-1.png");
    background-position: center;
    background-size: cover;
}
.spinner .face2 { 
    -webkit-transform: rotateY(90deg) translateZ(60px); 
    -ms-transform: rotateY(90deg) translateZ(60px); 
    transform: rotateY(90deg) translateZ(60px); 
    background-image: url("/public/assets/dice-2.png");
    background-position: center;
    background-size: cover;
}
.spinner .face3 { 
    -webkit-transform: rotateY(90deg) rotateX(90deg) translateZ(60px); 
    -ms-transform: rotateY(90deg) rotateX(90deg) translateZ(60px); 
    transform: rotateY(90deg) rotateX(90deg) translateZ(60px); 
    background-image: url("/public/assets/dice-3.png");
    background-position: center;
    background-size: cover;
}
.spinner .face4 { 
    -webkit-transform: rotateY(180deg) rotateZ(90deg) translateZ(60px); 
    -ms-transform: rotateY(180deg) rotateZ(90deg) translateZ(60px); 
    transform: rotateY(180deg) rotateZ(90deg) translateZ(60px); 
    background-image: url("/public/assets/dice-4.png");
    background-position: center;
    background-size: cover;
}
.spinner .face5 { 
    -webkit-transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px); 
    -ms-transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px); 
    transform: rotateY(-90deg) rotateZ(90deg) translateZ(60px); 
    background-image: url("/public/assets/dice-5.png");
    background-position: center;
    background-size: cover;
}
.spinner .face6 { 
    -webkit-transform: rotateX(-90deg) translateZ(60px); 
    -ms-transform: rotateX(-90deg) translateZ(60px); 
    transform: rotateX(-90deg) translateZ(60px); 
    background-image: url("/public/assets/dice-6.png");
    background-position: center;
    background-size: cover;
}

.spinner {
    -webkit-transform-style: preserve-3d;
    -ms-transform-style: preserve-3d;
    transform-style: preserve-3d;
    -webkit-transform-origin: 60px 60px 0;
    -ms-transform-origin: 60px 60px 0;
    transform-origin: 60px 60px 0;
    -webkit-transition: all .9s ease;
    -o-transition: all .9s ease;
    transition: all .9s ease;
    -webkit-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
	transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
}
.spinner.dice-1 {
	-webkit-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(0deg) rotateZ(0deg);
}
.spinner.dice-2 {
	-webkit-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(-90deg) rotateZ(0deg); 
}
.spinner.dice-3 {
    -webkit-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    -ms-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    -o-transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg);
    transform: rotateX(0deg) rotateY(-90deg) rotateZ(90deg); 
}
.spinner.dice-4 {
    -webkit-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    -ms-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    -o-transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg);
    transform: rotateX(0deg) rotateY(180deg) rotateZ(90deg); 
}
.spinner.dice-5 {
    -webkit-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    -ms-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    -o-transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg);
    transform: rotateX(0deg) rotateY(90deg) rotateZ(0deg); 
}
.spinner.dice-6 {
    -webkit-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    -ms-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    -o-transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg);
    transform: rotateX(90deg) rotateY(90deg) rotateZ(0deg); 
}
</style>