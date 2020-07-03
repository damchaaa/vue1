<template>
  <div >
    <h2> To do app</h2>
    <router-link to="/">Todos</router-link>
    <hr>
    <addtodo @add-todo="addTodo"></addtodo>
    <hr>
    <toDol1st
      v-if="todos.length"
      v-bind:todos="todos"
      v-on:remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import toDol1st from '@/components/todol1st'
import addtodo from '@/components/addTodo'
export default {
  name: 'App',
  data () {
    return {
      todos: [
        { id: 1, title: 'Купить 123', completed: false },
        { id: 2, title: 'Купить 456', completed: false },
        { id: 3, title: 'Купить 789', completed: false }
      ],
    }
  },
  components: {
    toDol1st,
    addtodo,
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo (todo) {
      this.todos.push(todo)
    }
  }
}
</script>
