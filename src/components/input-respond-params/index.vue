<template lang="pug">
  .wrap-input(v-if="value === 0")
    label(:style="`color: ${labelColor[index]}`") Диапазон {{ index + 1 }}
    .wrap-block-input
        .block-input
          label от
          input(type="text")

          label до
          input(type="text")
        .block-input
          label от
          input(type="text")

          label до
          input(type="text")
    .control-button
      button + Добавить диапазон
      button Удалить условие
</template>

<script>
	export default{
		name: 'input-responde-params',
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
      index: {
        type: Number,
        default(){
          return 0
        }
      }
		},
		data(){
			return{

			}
    },
    updated(){
      console.log(this.value, 'component imput respond params')
    }
	}
</script>

<style scoped>
  .wrap-input{
    display: grid;
		grid-template-columns: 200px 1fr;
    grid-template-rows: 1fr 1fr;
    grid-template-areas: "oneOneRow oneTwoRow" "twoOneRow twoTwoRow";
    grid-gap: 15px 15px;
		margin: 0 25px 25px 25px;
		align-items: center;
  }
  .control-button{
    grid-area: twoTwoRow;
  }
  input{
    width: 100px;
  }
</style>