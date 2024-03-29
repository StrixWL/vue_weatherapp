<script setup>
import Slider from './components/Slider.vue'
</script>

<template>
	<div class='layout'>
		<div class='container'>
			<header class='header'>
				<img src="./assets/logo.svg" class="logo" />
				<h1>Weather by brahim ツ</h1>
			</header>
			<div class="slider">
				<Slider />
			</div>
		</div>
	</div>
</template>

<style scoped>
.layout {
	width: 100vw;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
}

.container {
	background-color: rgba(255, 255, 255, .08);
	width: 80%;
	height: 80%;
	border-radius: 40px;
	box-shadow: rgba(0, 0, 0, 0.1) 0px 10px 50px;
	overflow: hidden;
}

.header {
	width: 100%;
	height: 75px;
	background-color: rgba(255, 255, 255, .2);
	display: flex;
	align-items: center;
}

.logo {
	height: 45px;
	margin: 15px;
	margin-left: 60px;
}

.header h1 {
	font-size: 17px;
	color: white;
	font-weight: 400;
	position: relative;
	top: 5px;
}

.slider {
	width: 100%;
	height: calc(100% - 75px);
	display: flex;
	justify-content: center;
	align-items: center;
}

</style>
