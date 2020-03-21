<template lang="pug">
  .wrap-component
    .respond-input
      label(:style="`color: ${labelColor[index]}`") Условие {{ index + 1 }}
      .wrap-select
        select(@change="selectValue($event)")
          template(v-for="(option, index) in arrSelect" :id="index")
            option(:value="index") {{ option }}
    input-respond-params(:value="inputRespondParam" :labelColor="labelColor[index]" :index="index")
    //- template(v-if="inputRespondParam === 0")
    //-   label(:style="`color: ${labelColor[index]}`") Диапазон {{ index + 1 }}
    //-   input-respond-params(:value="inputRespondParam")
    //- .control-button
    //-   button + Добавить диапазон
    //-   button Удалить условие
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
				inputRespondParam: 0
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
					if(el.selected) this.inputRespondParam = Number(el.value)
        })
        console.log(this.inputRespondParam)
			}
    }
	}
</script>

<style>
	.respond-input{
		display: grid;
		grid-template-columns: 200px 1fr;
    /* grid-template-rows: 1fr 1fr; */
    grid-template-areas: "oneOneRow oneTwoRow" "twoOneRow twoTwoRow" "threeOneRow threeTwoRow";
    /* grid-gap: 15px 15px; */
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