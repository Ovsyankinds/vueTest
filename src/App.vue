<template lang="pug">
  div#app
    .container
      .search
        Search
      .breadcrumbs
        Breadcrumbs
      .menu
        TopMenu
      .wrap-content
        router-view
</template>

<script>
/*eslint-disabled*/
import Vue from 'vue'
import VueRouter from 'vue-router'
import TopMenu from './components/top-menu'
import Search from './components/search'

Vue.use(VueRouter)

const Respond = () => import('./components/respond/index.vue')
const Parametres = () => import('./components/parametres/index.vue')
const Questions = () => import('./components/questions/index.vue')
const Logic = () => import('./components/logic/index.vue')
const Conditions = () => import('./components/conditions/index.vue')
const Breadcrumbs = () => import('./components/breadcrumbs/index.vue')

const router = new VueRouter({
  mode: 'history',
  linkActiveClass: "active",
  linkExactActiveClass: "exact-active",
  routes: [
    {path: '/respond', 'name': 'respond', component: Respond},
    {path: '/parametres', 'name': 'parametres',  component: Parametres},
    {path: '/questions', 'name': 'questions', component: Questions},
    {path: '/logic', 'name': 'logic', component: Logic},
    {path: '/conditions', 'name': 'conditions', component: Conditions},
    {path: '/breadcrumbs', 'name': 'breadcrumbs', component: Breadcrumbs},
  ]
})

export default {
  name: 'App',
  router,
  components: {
    TopMenu,
    Breadcrumbs,
    Search
  },
  data(){
    return {
      currentRouteName: null
    }
  },
  created(){
    this.$router.push('respond')
    // this.currentRouteName = this.$route.name
    // console.log(this.$route.name)
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .container{
    width: 850px;
    margin: 0 auto;
  }
  .wrap-content{
    width: 850px;
    height: 100%;
    border-top: 2px solid #B4FB0F;
    border-right: 1px solid white;
    border-left: 1px solid white;
    border-bottom: 1px solid white;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
    display: block;
    margin: 0 auto;
  }
</style>
