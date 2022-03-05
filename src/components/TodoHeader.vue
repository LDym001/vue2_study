<template>
  <div class="todo-header">
    <input type="text" @keyup.enter="add" placeholder="请输入一个小目标">
  </div>
</template>

<script>
export default {
  props: ['addTodo'],
  methods: {
    add(e) {
      this.addTodo(e.target.value)
      e.target.value = ''
    }
  }
}
</script>

<style>
  .todo-header {
    /* width: 100%; */
    height: 30px;
    margin: 3px;
  }
  .todo-header input {
    box-sizing: border-box;
    width: 100%;
    height: 100%;
    border: 1px solid #000;
    border-radius: 3px;
  }
</style>