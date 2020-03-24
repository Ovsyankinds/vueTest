<template lang="pug">
  .wrap-input
    .wrap-block-input(v-for="(item, index) in ageRespondCnt")
      label(v-if="index == 0" :style="`color: ${labelColor[index]}`") Диапазон {{ index + 1 }}
      label(v-else :style="`color: ${labelColor[index]}`") 
        span(class="or") или 
        | Диапазон {{ index + 1 }}
      .block-input
        label от
        input(type="text" :value="rangeOne" @blur="getValue($event, index)")

        label до
        input(type="text" :value="rangeTwo" @blur="getValue($event, index)")
    .control-button
      .item-control-button
      .item-control-button-add
        button(@click="addRound()") + Добавить диапазон
      .item-control-button-delete
        button(@click="deleteCondition") Удалить условие
</template>

<script>
  import InputCardType from '../input-card-type'

	export default{
    name: 'input-responde-params',
    components:{
      InputCardType
    },
		props: {
			value: {
				type: Number,
				default() {
					return 0
				}
      },
      labelColor: {
        type: String,
        default(){
          return 'green'
        }
      },
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
		data(){
			return{
        ageRespondCnt: 2,
        rangeOne: '',
        rangeTwo: '',
        inputAgeRespond: []
			}
    },
    methods: {
      addRound(){
        this.ageRespondCnt ++
      },
      deleteCondition(){
        this.$emit('deleteCondition')
      },
      getValue(event){
        if(Number(event.target.value)){
          this.inputAgeRespond.push(event.target.value)
        }
      }
    },
    watch: {
      submit: {
        immediate: true,
        handler(val){
          if(val === true){
            let size = 2;
            let subarray = [];
            for (let i = 0; i <Math.ceil(this.inputAgeRespond.length/size); i++){
                subarray[i] = this.inputAgeRespond.slice((i*size), (i*size) + size);
            }
            this.$emit('inputAgeRespond', subarray)
          }
        }
      }
    }
	}
</script>

<style scoped>
  .wrap-block-input{
    display: grid;
		grid-template-columns: 175px 1fr;
    grid-gap: 15px 15px;
		margin: 0 25px 25px 25px;
		align-items: center;
  }
  .block-input label {
    margin-right: 10px;
    margin-left: 10px;
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
    height: 25px;
  }
  .or{
    display: inline; 
    margin: 0 15px 0 0; 
    padding: 10px;
    background-color: #F2F8E6;
  }
</style>