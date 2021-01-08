<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}" >
       <p>
       <input type="checkbox" v-on:change="markComplete" >
        <button @click="$emit('del-todo', todo.id)"  class="del">x</button>
        {{todo.title}}</p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    data() {
    return {
      todos: this.todo,
    };
  },
  methods: {
    markComplete() {
      this.todos.completed = !this.todos.completed;
    },
  }
}
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 15px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete{
        text-decoration: line-through;
    }

    .del{
        background: #ff93f1;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>