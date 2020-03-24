<template lang="pug">
  .wrap-input
    .wrap-block-input(v-for="(item, index) in cardTypeCnt")
      label Тип {{ index + 1 }}
      .block-input
        select(@change="getValueSelect($event, index)")
          option(value="not") Выберите статус
          template(v-for="(option, indexCardType) in arrayCardType" :id="indexCardType")
            option(:value="option") {{ option }}
    .control-button
      .item-control-button
      .item-control-button-add
        button(@click="addRound()") + Добавить тип
      .item-control-button-delete
        button(@click="deleteCondition") Удалить условие
</template>

<script>
	export default{
		name: 'input-responde-params',
		data(){
			return{
        cardTypeCnt: 1,
        arrayCardType: ['Gold', 'Debet', 'Credit'],
        selectCardType: [],
			}
    },
    props: {
      indexCondition: {
        type: Number,
        default(){
          return 0
        }
      },
      submit: {
        type: Boolean,
        default(){
          return false
        }
      }
		},
    methods: {
      addRound(){
        this.cardTypeCnt ++
      },
       deleteCondition(){
        this.$emit('deleteCondition')
      },
      getValueSelect(event, indexType){
        event.target.options.forEach((el)=>{
          if(el.selected && el.value != 'not'){
            this.selectCardType[indexType] = el.value
          }
        })
      }
    },
    watch: {
      submit: {
        immediate: true,
        handler(val){
          if(val === true){
            this.$emit('valueCardType', this.selectCardType)
          }
        }
      }
    },
	}
</script>

<style scoped>
  .wrap-block-input{
    display: grid;
		grid-template-columns: 200px 1fr;
		margin: 0 25px 25px 25px;
		align-items: center;
  }
  .block-input select{
    width: 90%;
    height: 35px;
  }
  .control-button{
    display: grid;
    grid-template-columns: 200px 1fr 1fr;
    grid-gap: 15px 15px;
    grid-template-areas: "oneOneRow oneTwoRow oneThreeRow";
    align-items: center;
    margin-bottom: 25px;
  }
  .item-control-button-add{
    grid-area: oneThreeRow
  }
  .item-control-button-add{
    grid-area: oneTwoRow
  }
  input{
    width: 100px;
  }
  .or{
    display: inline; 
    margin: 0 15px 0 0; 
    padding: 10px;
    background-color: #F2F8E6;
  }
</style>