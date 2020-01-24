<template>
  <div id="app">
    <PageHeader></PageHeader>
    <PageContent></PageContent>
    <PageFooter></PageFooter>
  </div>
</template>

<script>
import PageHeader from './components/PageHeader.vue'
import PageContent from './components/PageContent.vue'
import PageFooter from './components/PageFooter.vue'

export default {
  name: 'app',
  components: {
    PageHeader,
    PageContent,
    PageFooter,
  }
}
</script>

<style lang="scss">

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 80%;
  background-color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
