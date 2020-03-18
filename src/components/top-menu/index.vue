<template lang="pug">
  div.wrap-top-menu
    ul
      template(v-for="(item, index) in topMenu" :id="index")
        router-link(v-if="index == 0" to="/parametres")
          li
            span {{ item }}
        router-link(v-else-if="index == 1" to="/questions")
          li
            span {{ item }}
        li(v-else)
          span {{ item }}
</template>

<script>
export default {
  data(){
    return{
      topMenu: ['Параметры', 'Вопросы', 'Логика', 'Условия', 'Респонденты']
    }
  }
}
</script>

<style scoped>
  .wrap-top-menu {
    width: 850px;
    margin: 0 auto;
  }
  .wrap-top-menu ul {
    height: 45px;
  }
  .wrap-top-menu ul li {
    display: inline-block;
  }
  .wrap-top-menu ul li span{
    width: 100px;
    color: green;
  }
</style>