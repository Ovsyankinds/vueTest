<template lang="pug">
  .wrap-input
    .wrap-block-input(v-for="(item, index) in cardStatusCnt")
      label Статус {{ index + 1 }}
      .block-input
        select
          option(value="11")
          option(value="22")
          option(value="33")
    .control-button
      .item-control-button
      .item-control-button-add
        button(@click="addRound()") + Добавить статус
      .item-control-button-delete
        button(@click="deleteCondition") Удалить условие
</template>

<script>
	export default{
    name: 'input-responde-params',
    props: {
      indexCondition: {
        type: Number,
        default(){
          return 0
        }
      }
		},
		data(){
			return{
        cardStatusCnt: 1
			}
    },
    methods: {
      deleteCondition(){
        console.log('deleteCondition component input age respond')
        this.$emit('deleteCondition', this.indexCondition)
      }
    }
	}
</script>

<style scoped>
  .wrap-block-input{
    display: grid;
		grid-template-columns: 200px 1fr;
    grid-gap: 15px 15px;
		margin: 0 25px 25px 25px;
		align-items: center;
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