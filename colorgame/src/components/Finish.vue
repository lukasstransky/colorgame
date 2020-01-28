<template>
  <div class="hello">
    <p style="font-size: 20vh">🎉{{score}} Punkte!🎉</p>
    <h1 v-if="isHighscore" style="font-size: 5vh; margin-top: -15vh">
        Neuer Highscore!
    </h1>
    <h1 v-if="!isHighscore" style="font-size: 5vh; margin-top: -15vh">
        Kein Highscore!
    </h1>
    <button class="myButton" v-on:click="$emit('backToStart')">Zurück zum Start</button>
  </div>
</template>

<script>
export default {
  name: 'FinishScreen',
  props: {
    score: Number,
    isHighscore: Boolean
  }
}
</script>

<style scoped>
.myButton {
	box-shadow: 0px 8px 14px -7px #276873;
	background:linear-gradient(to bottom, #599bb3 5%, #408c99 100%);
	background-color:#599bb3;
	border-radius:11px;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Verdana;
	font-size:28px;
	font-weight:bold;
	padding:12px 20px;
	text-decoration:none;
	text-shadow:0px 0px 0px #3d768a;
}
.myButton:hover {
	background:linear-gradient(to bottom, #408c99 5%, #599bb3 100%);
	background-color:#408c99;
}
.myButton:active {
	position:relative;
	top:1px;
}
</style>