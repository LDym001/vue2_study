<template>
  <div class="todo-footer">
    <input type="checkbox" @change="cAll" :checked="isCheckAll" id="checkAll">
    <label for="checkAll">全选</label>
    <span>已选{{completeCount}}/{{todos.length}}</span>
  </div>
</template>

<script>
export default {
  props: ['todos','checkAll'],
  computed: {
    completeCount() {
      return this.todos.filter(todo => todo.isComplete).length
    },
    isCheckAll() {
      return this.completeCount === this.todos.length && this.todos.length > 0
    }
  },
  methods: {
    cAll(e) {
      this.checkAll(e.target.checked)
    }
  }
}
</script>

<style>
  .todo-footer {
    margin: 3px;
    height: 30px;
    box-sizing: border-box;
    border: 1px solid #000;
    border-radius: 3px;
  }
  span {
    margin-left: 10px;
  }
</style>