<template lang="pug">
  div#app
    div.search
    div.menu
      TopMenu
    div.wrap-content
      router-view
</template>

<script>
/*eslint-disabled*/
import TopMenu from './components/top-menu'
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)

const Index = () => import('./components/respond/index.vue')
const Parametres = () => import('./components/parametres/index.vue')
const Questions = () => import('./components/questions/index.vue')

const router = new VueRouter({
  mode: 'history',
  routes: [
    {path: '/', component: Index},
    {path: '/parametres', component: Parametres},
    {path: '/questions', component: Questions}
  ]
})

export default {
  name: 'App',
  router,
  components: {
    TopMenu
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .wrap-content{
    width: 850px;
    height: 100%;
    border-top: 2px solid yellow;
    border-right: 1px solid white;
    border-left: 1px solid white;
    border-bottom: 1px solid white;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
    display: block;
    margin: 0 auto;
  }
</style>
