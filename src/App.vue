<template>
  <div id="app">
    <div class="frame">
      <app-header></app-header>
      <app-input @addItem="addTextItem"></app-input>
      <app-item v-for="todo in todos" v-bind:todo="todo" @removeItem="removeTextItem" :key="todo.id"></app-item>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Input from './components/Input.vue';
  import Item from './components/Item.vue';

  export default {
    data() {
      return {
        todos: [
          {id: 0, text: "Play soccer."},
          {id: 1, text: "Play basketball."},
          {id: 2, text: "Play handball."}
        ],
        nextId: 3
      }
    },
    components: {
      appHeader: Header,
      appInput: Input,
      appItem: Item
    },
    methods: {
      addTextItem(inputText) {
        this.todos.push({id: this.nextId, text: inputText});
        this.nextId++;
      },
      removeTextItem(id) {
        const todos = this.todos;
        this.todos = todos.filter(function(todo) { return todo.id != id });
      }
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
