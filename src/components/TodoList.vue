<template>
    <b-card
        title="Todos"

    >
        <add-todo v-on:added-todo="addNewTodo"></add-todo>
        <b-table striped hover :items="todos"></b-table>
    </b-card>
</template>

<script>

/* eslint-disable no-console */

// import Todo from './components/Todo'
import AddTodo from './AddTodo'

export default {

    data() {
        return {
            todos: [
                {id: 0, name: "Learn Vue.js", done: false}
            ]
        }
    }, 
    components: {
        AddTodo
    },
    methods: {
        addNewTodo(todo) {
            console.log('new todo!!', todo)
            let {todos} = this
            
            const todoIndex = todos.length
            
            let newTodo = {
                id: todoIndex,
                name: todo.name,
                done: todo.done
            }

            todos.push(newTodo)
            this.todos = todos
        }
    }
}
</script>
