<template lang="pug">
  .wrap
    span.end(v-if="indexCondition != 0" :style="`background-color: ${labelColor[indexCondition]}`") И
    .wrap-component-select
      label(:style="`color: ${labelColor[indexCondition]}`") Условие {{ indexCondition + 1 }}
      .select(@change="selectValue($event, indexCondition)")
        select(:data-idSelect="indexCondition" :id="`selected-condition-${indexCondition}`")
          template(v-for="(option, index) in arrSelect" :id="index")
            option(:value="index") {{ option }}
</template>

<script>
  export default {
    name: 'input-selected',
    data(){
      return{
        arrSelect: ['Возраст респондента', 'Тип карты лояльности', 'Статус карты лояльности'],
        type: 0
      }
    },
    props: {
      indexCondition: {
        type: Number,
        default(){
          return 0
        }
      },
      labelColor: {
        type: Array
      },
      backgroundColor: {
        type: Array
      }
    },
    methods: {
      selectValue(event, indexCondition){
        event.target.options.forEach((el)=>{
          if(el.selected && indexCondition == Number(event.srcElement.dataset.idselect)){
            this.type = Number(el.value)
            this.$emit('type', this.type)
          }
        })
      }
    }
  }
</script>

<style scoped>
  .wrap-component-select {
    display: grid;
		grid-template-columns: 200px 1fr;
		margin: 0 25px 25px 25px;
		align-items: center;
  }
  .wrap-component-select .select select{
		width: 100%;
		height: 35px;
	}
  .end {
    width: 10px;
    height: 17px;
    position: relative;
    margin: 0;
    left: 25px;
    top: -18px;
    background-color: blue;
    padding: 8px 15px;
    border-radius: 10%;
  }
</style>