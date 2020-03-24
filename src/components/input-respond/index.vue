<template lang="pug">
  .wrap-conditions
    .condition-item(v-for="(item, indexCondition) in countCondition.length" :id="indexCondition")
      .respond-input
        InputSelectRespond(
          :indexCondition="indexCondition" 
          @deleteCondition="deleteCondition" 
          :labelColor="labelColor" 
          :backgroundColor="backgroundColor"
          :submit="submit"
          @valueCardType="valueCardType"
          @valueCardStatus="valueCardStatus"
        )
    button.addConditions(@click="addConditions()") Добавить условие +
    button.sumbit(@click="submitConditions()") Далее
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
        countCondition: [],
        labelColor: ['#D1A632', '#556ECB', '#92B960', '#C96661'],
        backgroundColor: ['#F8ECCB', '#C2CEFA', '#D9FCAB', '#FFC8C5'],
        submit: true,
        cardType: [],
        cardStatus: [],
        submitArr: []
			}
		},
		methods: {
      addConditions(){
        if((this.countCondition.length) != 0 && (this.countCondition.length) % 4 == 0){
          this.labelColor = this.labelColor.concat(this.labelColor)
          this.backgroundColor = this.backgroundColor.concat(this.backgroundColor)
        }
        this.countCondition.push(`'Условие ${this.cnt++}'`)
      },
      deleteCondition(indexConditionItem){
        this.countCondition.splice(indexConditionItem, 1)
        this.cnt -= 1
      },
      restartIndexForColor(){
        this.indexForColor = 0
      },
      submitConditions(){
        this.submit = true
        console.log( this.submitArr, 'submit array')
      },
      valueCardType(value){
        this.cardType.push(value)
        this.submitArr.cardType = this.cardType
      },
      valueCardStatus(value){
        this.cardStatus.push(value)
        this.submitArr.cardStatus = this.cardStatus
      }
    }
	}
</script>

<style>
	.addConditions, .sumbit{
    display: block;
    width: 150px;
    margin: 45px auto 25px auto;
  }
</style>