<template>
    <span>
        <b-button v-b-modal.modal-1 variant="success" class="float-right">Add Todo</b-button>

        <b-modal id="modal-1" title="New Todo" @ok="handleOk">
            <b-form @submit="onSubmit" @submit.stop.prevent="onSubmit">
                <b-form-group
                    id="todo"
                    label="Todo Name"
                    label-for="todo"
                    description="Enter the todo you would like to add."
                    invalid-feedback="Todo is required"
                >
                    <b-form-input
                    id="todo"
                    v-model="todo.name"
                    type="text"
                    required
                    placeholder="Enter Todo"
                    ></b-form-input>
                </b-form-group>
            </b-form>
        </b-modal>
    </span>
</template>

<script>
    export default {
        data() {
            return {
                todo: {
                    name: "",
                    done: false
                }
            }
        }, 
        methods: {
            
            validateForm() {
                if(this.todo.name == "") return false
                return true
            },

            handleOk(bvModalEvt) {
                bvModalEvt.preventDefault()
                this.onSubmit()
            },

            onSubmit() {
                if(this.validateForm()) {
                    this.$emit("added-todo", this.todo)
                    
                    this.$nextTick(() => {
                        this.$bvModal.hide('modal-1')
                        this.todo.name = ""
                    })

                } else return
            }
        }
    }
</script>
