<template>
	<header>
		<a class="logo" href="/">
			<img alt="Site logo" src="./assets/gift-box-white.svg">
		</a>
		<h1>{{$translate('secret-santa')}}</h1>
	</header>
	<main>
		<FriendList v-if="!hasUser()"/>
		<FriendSecretPage v-if="hasUser()"/>
	</main>
	<!-- <footer >
		<a href="https://github.com/alexsad/secret-friend-list">github project</a>
	</footer> -->
</template>

<script lang="ts">
import FriendList from './components/friend-list/friend-list.vue';
import FriendSecretPage from './components/friend-secret-page/friend-secret-page.vue';

export default {
	components:{
		FriendList,
		FriendSecretPage,
	},
	methods: {
		hasUser(){
			const urlParams = new URLSearchParams(window.location.search);
			return urlParams.has('user');
		}
	},
}
</script>

<style lang="scss">
body, html{
	padding: 0;
	margin: 0;
	box-sizing:border-box;
}
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	box-sizing:border-box;
	display: grid;
	grid-template-columns: 1fr;
	grid-template-rows: 15vh 85vh;
	grid-template-areas:"header" "main";
	// grid-gap:16px;

	> header {
		background-color: purple;
		color: #efefef;
		grid-area:header;
		position: relative;

		> a.logo{
			position: absolute;
			bottom: -16%;
			left: 16px;
			> img{
				width: 85px;
			}
		}

		> h1{
			margin: 0;
			position: absolute;
			top: 50%;
			width: 100%;
			text-align: center;
			transform: translateY(-50%);
		}
	}

	> main{
		width: 400px;
		margin: 0px auto;
		grid-area:main;
	}
	> footer{
		grid-area:footer;
		background-color: purple;
		display: table;
		height: 100%;

		> a {
			display: table-cell;
			color: #efefef;
			width:100%;
			height: 100%;
			text-align: center;
			vertical-align: middle;
		}
	}
}
</style>
