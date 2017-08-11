<template>
  <div id="app">

    <meu-menu :routes="routes"/>

    <transition name="page">
      <router-view></router-view>
    </transition>

  </div>
</template>

<script>
  import { routes }  from './routes';
  import Menu from './components/shared/menu/Menu.vue';

  export default {
    components: {
      'meu-menu' : Menu
    },
    data() {
      return {
        routes
      }
    }

  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  h1, h2 {
    font-weight: normal;
  }

  .page-enter-active, .page-leave-active {
    transition: opacity .3s
  }
  .page-enter, .page-leave-active {
    opacity: 0
  }
</style>
