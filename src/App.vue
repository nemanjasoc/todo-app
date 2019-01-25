<template>
  <div id="app">
    <div class="frame">
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
          {id: 1, text: "Play soccer."},
          {id: 2, text: "Play basketball."},
          {id: 3, text: "Play handball."},
          {id: 4, text: "Sport #4."},
          {id: 5, text: "Sport #5."},
          {id: 6, text: "Sport #6."},
          {id: 7, text: "Sport #7."},
          {id: 8, text: "Sport #8."},
          {id: 9, text: "Sport #9."},
          {id: 10, text: "Sport #10."},
          {id: 11, text: "Sport #11."},
          {id: 12, text: "Sport #12."},
          {id: 13, text: "Sport #13."},
          {id: 14, text: "Sport #14."}
        ],
        nextId: 15,
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
    min-height: 410px;
    border: 5px solid black;
    text-align: center;
    background: #00805da3;
  }
</style>
