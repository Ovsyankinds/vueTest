<template lang="pug">
  .wrap-select-input
    .wrap-select
      label(:style="`color: ${labelColor[indexCondition]}`") Условие {{ indexCondition + 1 }}
      .select(@change="selectValue($event, indexCondition)")
        select(:data-idSelect="indexCondition" :id="`selected-condition-${indexCondition}`")
          template(v-for="(option, index) in arrSelect" :id="index")
            //- option(v-if="index==0" :value="index" selected) {{ option }}
            option(:value="index") {{ option }}
    InputAgeRespond(v-if="type == 0" :index="indexCondition" @deleteCondition="deleteCondition")
    InputCardType(v-else-if="type == 1" :index="indexCondition" @deleteCondition="deleteCondition")
    InputCardStatus(v-else-if="type == 2" :index="indexCondition" @deleteCondition="deleteCondition")
</template>

<script>
  import InputAgeRespond from '../input-age-respond'
  import InputCardType from '../input-card-type'
  import InputCardStatus from '../input-card-status'

  export default {
    name: 'input-selected-respond',
    components:{
      InputAgeRespond,
      InputCardType,
      InputCardStatus
    },
    data(){
      return{
        arrSelect: ['Возраст респондента', 'Тип карты лояльности', 'Статус карты лояльности', 'Выберите условие'],
        labelColor: ['brown', 'blue', 'green', 'red'],
        type: 0
      }
    },
    props: {
      indexCondition: {
        type: Number,
        default(){
          return 0
        }
      }
    },
    methods: {
      selectValue(event, indexCondition){
        event.target.options.forEach((el)=>{
          if(el.selected && indexCondition == Number(event.srcElement.dataset.idselect)){
            this.type = Number(el.value)
          }
        })
      },
      deleteCondition(indexConditionItem){
        console.log('deleteCondition component input select respond')
        this.$emit('deleteCondition', indexConditionItem)
      }
    }
  }
</script>

<style scoped>
  .wrap-select {
    display: grid;
		grid-template-columns: 200px 1fr;
		margin: 0 25px 25px 25px;
		align-items: center;
  }
  .select select{
		width: 100%;
		height: 35px;
	}
</style>