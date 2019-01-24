<template>
  <div id="app">
    <div class="frame">
      <app-header></app-header>
      <app-input></app-input>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Input from './components/Input.vue';

  export default {
    components: {
      appHeader: Header,
      appInput: Input
    }
  }
</script>

<style>
  .app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .frame {
    margin: 20px auto 20px auto;
    width: 425px;
    min-height: 600px;
    border: 5px solid black;
    text-align: center;
    background: #00805da3;
  }
</style>
