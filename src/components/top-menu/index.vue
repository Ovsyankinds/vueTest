<template lang="pug">
  .wrap-top-menu
    router-link(v-for="(item, index) in topMenu" :to="item.url") {{ item.nameUrl }}
</template>

<script>
export default {
  data(){
    return{
      topMenu: [
        {
          nameUrl: 'Параметры',
          url: '/parametres'
        },
        {
          nameUrl: 'Вопросы',
          url: '/questions'
        },
        {
          nameUrl: 'Логика',
          url: '/logic'
        },
        {
          nameUrl: 'Условия',
          url: '/conditions'
        },
        {
          nameUrl: 'Респонденты',
          url: '/respond'
        }
      ]
    }
  }
}
</script>

<style scoped>
  .wrap-top-menu {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    text-align: center;
  }
  .wrap-top-menu a {
    height: 35px;
    color: green;
    text-decoration: none;
    padding-bottom: 10px;
  }
  .wrap-top-menu .exact-active {
    color: black;
    font-weight: bold;
    border-bottom: 3px solid #76972A
  }
</style>