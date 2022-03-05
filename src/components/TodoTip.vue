<template>
  <div class="todo-box">
    <todo-header :addTodo="addTodo"/>
    <todo-item :todos="todos" :delTodo="delTodo" :changeStatus="changeStatus"/>
    <todo-footer :todos="todos" :checkAll="checkAll"/>
  </div>
</template>

<script>
import {nanoid} from 'nanoid'
import TodoFooter from './TodoFooter.vue'
import TodoHeader from './TodoHeader.vue'
import TodoItem from './TodoItem.vue'

export default {
  components: {
    TodoHeader,
    TodoFooter,
    TodoItem 
  },
  data() {
    return {
      todos: [
        // {id: "001",value: "学习",isComplete: true},
        // {id: "002",value: "吃饭",isComplete: false},
        // {id: "003",value: "睡觉",isComplete: true},
      ]
    }
  },
  methods: {
    delTodo(id) {
      this.todos = this.todos.filter( todo => todo.id!=id )
    },
    addTodo(name) {
      this.todos.unshift({id: nanoid(),value: name,isComplete: false})
    },
    changeStatus(id) {
      this.todos.forEach(todo => {
          if (todo.id===id) {
            todo.isComplete = !todo.isComplete
          }
        })
    },
    checkAll(isCheckAll) {
      this.todos.forEach(todo => {todo.isComplete = isCheckAll})
    }
  }
}
</script>

<style>
  .todo-box {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    min-height: 75px;
    width: 500px;
    margin: 0 auto;
    background-color: skyblue;
    border: 1px solid black;
    border-radius: 5px;
}
</style>