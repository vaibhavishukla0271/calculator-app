<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Calculator from './components/Calculator.vue';

// add compomnent here
@Component({
  components: {
    Calculator,
  },
})
export default class App extends Vue {}
</script>
