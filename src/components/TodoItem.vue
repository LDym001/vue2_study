<template>
  <div class="todo-item">
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <input :id="todo.id" type="checkbox" @change="cStatus(todo.id)" :checked="todo.isComplete" >
        <label :for="todo.id">{{todo.value}}</label>
        <button @click="del(todo.id)">删除</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['todos','delTodo','changeStatus'],
  methods: {
    del(id) {
      this.delTodo(id)
    },
    cStatus(id) {
      this.changeStatus(id)
    }
  }
}
</script>

<style>
  ul {
    margin: 3px;
    padding: 0;
  }
  li {
    list-style: none;
    height: 30px;
  }
  li:hover button {
    visibility: visible;
  }
  button {
    float: right;
    visibility: hidden;
    margin-right: 3px;
    width: 55px;
    border-radius: 3px;
    border: 1px solid rgba(0, 0, 0, .2);
    text-align: center;
    background-color: pink;
    cursor: pointer;
  }
</style>