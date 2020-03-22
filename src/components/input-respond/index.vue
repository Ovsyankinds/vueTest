<template lang="pug">
  .wrap-conditions
    .condition-item(v-for="(item, indexCondition) in countCondition.length" :id="indexCondition")
      .respond-input
        InputSelectRespond(:indexCondition="indexCondition" @deleteCondition="deleteCondition")
    button.addConditions(@click="addConditions()") Добавить условие +
</template>

<script>
  import InputSelectRespond from '../input-select-respond'
	export default{
		name: 'input-respond',
		components:{
      InputSelectRespond
		},
		data() {
			return{
        cnt: 1,
        countCondition: []
			}
		},
		methods: {
      addConditions(){
        // this.countCondition ++
        this.countCondition.push(this.cnt++)
         console.log(this.countCondition, 'addConditions component input respond')
      },
      deleteCondition(indexConditionItem){
        console.log(indexConditionItem, 'deleteCondition component input respond')
        this.countCondition.splice(indexConditionItem, 1)
        this.cnt -= 1
        console.log(this.countCondition, 'addConditions show component input respond')
        // this.countCondition --
      },
      updated(){
        console.log(this.countCondition)
      }
    }
	}
</script>

<style>
	.addConditions{
    display: block;
    width: 150px;
    margin: 45px auto 25px auto;
  }
</style>