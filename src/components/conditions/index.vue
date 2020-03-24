<template lang="pug">
  div.wrap-conditions
    span.headerSpan Добавить условия
    .wrap-one
      .nav
        span Nav
        TopMenu(class="nav-top-menu" :vertical="true")

      .wrap-two
        .header
          span Header
        .content
          span Content
        .footer
          span Footer
</template>

<script>
  import TopMenu from '../top-menu'
  export default {
    name: 'conditions',
    components: {TopMenu}
  }
</script>

<style scoped>
  .wrap-conditions{

  }
  .headerSpan{
    margin: 25px;
    text-align: left;
  }
  span {
    margin: 0;
    text-align: center;
  }
  .wrap-one {
    display: grid;
    grid-template-columns: 1fr 1fr; 
  }
  .nav-top-menu ul li{
    display: inline;
  }
  .wrap-two {
    display: grid;
    grid-template-rows: 1fr 1fr 1fr; 
  }
</style>