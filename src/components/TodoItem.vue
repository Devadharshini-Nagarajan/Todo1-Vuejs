<template>
  <div class="todo-item" v-bind:class="{'is-complete': todo.completed}">
    <input type="checkbox" v-on:change="changeComplete" />
    <p>
      {{todo.title}}
      <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    changeComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: lightgray;
  border-bottom: 1px solid black;
  padding: 10px;
}
.is-complete {
  text-decoration: line-through;
}
.del {
  background: coral;
  color: white;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>