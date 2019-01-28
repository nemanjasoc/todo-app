<template>
  <div id="app">
    <app-header></app-header>
    <app-input @addItem="addTextItem"></app-input>
    <app-item
      v-for="todo in visibleTodoItems" 
      v-bind:todo="todo"
      @removeItem="removeTextItem"  
      :key="todo.id">
    </app-item>
    <app-pagination 
      v-bind:todos="todos" 
      v-bind:currentPage="currentPage"
      v-bind:pageSize="pageSize"
      @updatePage="updatePage">
    </app-pagination>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Input from './components/Input.vue';
  import Item from './components/Item.vue';
  import Pagination from './components/Pagination.vue';

  export default {
    data() {
      return {
        todos: [
          {id: 1, text: "Get up at 7 am."},
          {id: 2, text: "Get a fire."},
          {id: 3, text: "Learn programming."},
          {id: 4, text: "Make a lunch."},
          {id: 5, text: "Wash car."},
          {id: 6, text: "Todo #6."},
          {id: 7, text: "Todo #7."},
          {id: 8, text: "Todo #8."},
          {id: 9, text: "Todo #9."},
          {id: 10, text: "Todo #10."},
          {id: 11, text: "Todo #11."}
        ],
        nextId: 12,
        currentPage: 0,
        pageSize: 3,
        visibleTodoItems: []
      };
    },
    components: {
      appHeader: Header,
      appInput: Input,
      appItem: Item,
      appPagination: Pagination
    },
    beforeMount: function() {
      this.updateVisibleTodoItems();
    },
    methods: {
      addTextItem(inputText) {
        this.todos.push({id: this.nextId, text: inputText});
        this.nextId++;
        this.updateVisibleTodoItems();
      },
      removeTextItem(id) {
        const todos = this.todos;
        this.todos = todos.filter(function(todo) { return todo.id != id });
        this.updateVisibleTodoItems();
      },
      updatePage(pageNumber) {
        this.currentPage = pageNumber;
        this.updateVisibleTodoItems();
      },
      updateVisibleTodoItems() {
        this.visibleTodoItems = this.todos.slice(this.currentPage * this.pageSize, (this.currentPage * this.pageSize) + this.pageSize);

        if (this.visibleTodoItems.length == 0 && this.currentPage > 0) {
          this.updatePage(this.currentPage - 1)
        }
      }
    }
  }
</script>

<style>
  body {
    background: #7FDBFF;
    background-image: linear-gradient(to right, #0040ffbd, #008004b5);
    display: flex;
    justify-content: center;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    margin-top: 140px;
  }
</style>
