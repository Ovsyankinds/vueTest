<template lang="pug">
  .wrap-breadcrumbs
    ul
      li
        span Домой
      li.arrow -> 
      li
        span {{realNameCrumb }}
      li.arrow ->
      li
        //- ниже условие v-show для того, чтоб работал вывод lastCrumb - надо разобраться, почему
        span(v-show="false") {{ this.$route.name }}
        span {{ this.lastCrumb }}
</template>

<script>
  export default {
    data(){
      return {
        arrNameCrumbs: [
          {
            ruName: 'Респонденты',
            enName: 'respond',
            lastCrumb: 'Добавить опрос'
          },
          {
            ruName: 'Условия',
            enName: 'conditions',
            lastCrumb: 'Добавить условия'
          },
          {
            ruName: 'Логика',
            enName: 'logic',
            lastCrumb: 'Добавить логику'
          },
          {
            ruName: 'Вопросы',
            enName: 'questions',
            lastCrumb: 'Добавить вопросы'
          },
          {
            ruName: 'Параметры',
            enName: 'parametres',
            lastCrumb: 'Добавить параметры'
          },
        ],
        realNameCrumb: null,
        lastCrumb: null
      }
    },
    created(){
      this.realNameCrumb = this.arrNameCrumbs[0].ruName
      this.lastCrumb = this.arrNameCrumbs[0].lastCrumb
    },
    updated(){
      // console.log(this.$route, 'update components breadcrumbs')  
      this.arrNameCrumbs.forEach((item)=>{
        if(item.enName == this.$route.name){
          this.realNameCrumb = item.ruName
          this.lastCrumb = item.lastCrumb
        }
      })
    }
  }
</script>

<style scoped>
  .wrap-breadcrumbs {
    margin-left: -30px;
  }
  .wrap-breadcrumbs ul li{
    display: inline-block;
  }
  .wrap-breadcrumbs ul .arrow{
    margin-left: 10px;
    margin-right: 10px;
  }
  .wrap-breadcrumbs span{
    display: block;
    margin: 0;
    font-size: 12px;
    width: auto;
  }
</style>