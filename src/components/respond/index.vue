<template lang="pug">
	.div.wrap-respond
		span Добавить опрос
		template(v-for="(input, index) in arrSelect.length" :id="index")
			input-respond(
				:arrSelect="arrSelect" 
				:index="index"
				:labelColor="labelColor"
			)
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
				// countRespond: 4,
				arrSelect: ['Возраст респондента', 'Тип карты лояльности', 'Статус карты лояльности', 'Выберите условие'],
				labelColor: ['yellow', 'blue', 'green', 'red']
			}
		}
	}
</script>

<style>
	.wrap-respond {
		width: 850px;
		height: 100%;
		border: 1px solid grey;
		display: block;
		margin: 0 auto;
	}

	span {
		width: 100%;
		display: block;
		text-align: left;
		margin: 25px 25px;
		color: grey;
	}
</style>