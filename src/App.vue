<template>
  <div id="app">
    <Operator></Operator>
    <Resultado></Resultado>
  </div>
</template>

<script>
import Operator from './components/Operator'
import Resultado from './components/Resultado'

export default {
  name: 'App',
  components: {
    Operator, Resultado
  }
}
</script>

<style>

</style>
