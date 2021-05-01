<template>
  <div>
    <h2>Todo application</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo
        @add-todo="addTodo"
    />
    <hr>
    <TodoList
        v-bind:todos="todos"
        @remove-todo="removeTodo" />
  </div>
</template>


<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Take a Christmas Market Cruise Through Europe', completed: false},
        {id: 2, title: 'Make a Wish in the Trevi Fountain in Italy', completed: false},
        {id: 3, title: 'See the Changing of the Guard in London', completed: false}
      ]
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList, AddTodo
  }
}
</script>