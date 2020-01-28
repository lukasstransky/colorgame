<template>
  <div>
    <p style="font-size: 20vh">
		<span style='color: green'>C</span>
		<span style='color: blue'>O</span>
		<span style='color: purple'>L</span>
		<span style='color: yellow'>O</span>
		<span style='color: red'>R</span>
		<br>
		<span style='color: yellow'>G</span>
		<span style='color: purple'>A</span>
		<span style='color: blue'>M</span>
		<span style='color: green'>E</span>
	</p>
	<p> </p>
    <h2 style="font-size: 5vh; margin-top: -20vh">👑: {{currentHighscore}} Punkte</h2>
    <button v-on:click="$emit('startGame')" class="myButton">Start Game</button>
  </div>
</template>

<script>
export default {
  name: 'StartScreen',
  props: {
    currentHighscore: Number
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
