<template>
  <AppHeader/>
  <AppIndex/>
  <AppFooter/>
</template>

<script>
  import AppHeader from './components/header/app-header'
  import AppIndex from './components/index/app-index'
  import AppFooter from './components/footer/app-footer'

  export default {
    name: 'App',
    components: {
      AppHeader,
      AppIndex,
      AppFooter
    }
  }
</script>

<style>

</style>
