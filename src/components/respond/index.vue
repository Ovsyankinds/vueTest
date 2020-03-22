<template lang="pug">
	.wrap-respond
		span Добавить опрос
		input-respond
</template>

<script>
	import InputRespond from "../input-respond"
	export default{
		name: 'respond',
		components: {
			InputRespond
		},
		data(){
			return{
			}
		}
	}
</script>

<style>
	span {
		width: 100%;
		display: block;
		text-align: left;
		margin: 25px 25px;
		color: grey;
	}
</style>