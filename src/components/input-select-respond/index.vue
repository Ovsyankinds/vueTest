<template lang="pug">
  .wrap-select-input(:style="`background-color: ${backgroundColor[indexCondition]}`")
    div.empty(v-if="indexCondition == 0")
    .wrap-select
      InputSelect(:indexCondition="indexCondition" :labelColor="labelColor" @type="typeCondition" :backgroundColor="backgroundColor")
    InputAgeRespond(v-if="type == 0" :index="indexCondition" @deleteCondition="deleteCondition(indexCondition)" :submit="submit")
    InputCardType(
      v-else-if="type == 1" 
      :index="indexCondition" 
      @deleteCondition="deleteCondition(indexCondition)" 
      :submit="submit" 
      @valueCardType="valueCardType"
    )
    InputCardStatus(
      v-else-if="type == 2" 
      :index="indexCondition"
      @deleteCondition="deleteCondition(indexCondition)" 
      :submit="submit"
      @valueCardStatus="valueCardStatus"
    )
</template>

<script>
  import InputAgeRespond from '../input-age-respond'
  import InputCardType from '../input-card-type'
  import InputCardStatus from '../input-card-status'
  import InputSelect from '../input-select'

  export default {
    name: 'input-selected-respond',
    components:{
      InputAgeRespond,
      InputCardType,
      InputCardStatus,
      InputSelect
    },
    data(){
      return{
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
      },
      submit: {
        type: Boolean
      }
    },
    methods: {
      typeCondition(type){
        this.type = type
      },
      deleteCondition(indexConditionItem){
        this.$emit('deleteCondition', indexConditionItem)
      },
      valueCardType(value){
        this.$emit('valueCardType', value)
      },
      valueCardStatus(value){
        this.$emit('valueCardStatus', value)
      }
    }
  }
</script>

<style scoped>
  .wrap-select-input{
    border-top: 1px solid grey;
    padding-bottom: 5px;
  }
  .empty{
    margin-bottom: 30px;
  }
</style>