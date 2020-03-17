<template lang="pug">
	div.respond-input
		label(:style="`color: ${labelColor[index]}`") Условие {{ index + 1 }}
		div.wrap-select
			select(@change="selectValue($event)")
				template(v-for="(option, index) in arrSelect" :id="index")
					option(:value="index") {{ option }}
			input-respond-params(:value="inputRespondParam")
</template>

<script>
	import InputRespondParams from '../input-respond-params'
	export default{
		name: 'input-respond',
		components:{
			InputRespondParams
		},
		data() {
			return{ 
				inputRespondParam: null
			}
		},
		props: {
			arrSelect: {
				type: Array,
				default(){
					return ['Возраст респондента']
				}
			},
			index: {
				type: Number,
				default(){
					return 1
				}
			},
			labelColor: {
				type: Array,
				default(){
					return ['grey']
				}
			}
		},
		methods: {
			selectValue(event){
				event.target.options.forEach((el)=>{
					if(el.selected) this.inputRespondParam = el.value
				})
			}
		}
	}
</script>

<style>
	.respond-input{
		display: grid;
		grid-template-columns: 200px 1fr;
		margin: 0 25px 25px 25px;
		align-items: center;
	}
	.respond-input label {
		text-align: left;
	}
	.respond-input select{
		width: 100%;
		height: 35px;
	}
</style>