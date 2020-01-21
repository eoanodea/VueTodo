<template>
    <b-card
        title="Todos"

    >
        <add-todo v-on:added-todo="addNewTodo"></add-todo>
        <b-table striped hover :items="todos">
            <template v-slot:cell(done)="data">
                <b-button variant="success" v-if="!data.value" @click="completeTodo(data.index, true)">Done</b-button> 
                <b-button variant="danger" v-else @click="completeTodo(data.index, false)">Not Done</b-button>
            </template>
        </b-table>
    </b-card>
</template>

<script>
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
            let {todos} = this
            
            const todoIndex = todos.length
            
            let newTodo = {
                id: todoIndex,
                name: todo.name,
                done: todo.done
            }

            todos.push(newTodo)
            this.todos = todos
        },

        completeTodo(index, bool) {
            let {todos} = this
            
            todos[index].done = bool

            this.todos = todos
        }
    }
}
</script>
