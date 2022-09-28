<template>
<div style="width: 700px;">
    <div style="display:inline-block;">
        <b-form-input type="text" v-model="newTodoItem" ></b-form-input> 
    </div>
    <div style="display:inline-block;">
        <b-button v-on:click="addTodo" variant="outline-primary">add</b-button>
    </div>
</div>
</template>

<script>
export default {
    data(){
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo(){
            // Remove front and back space strings of text entered in inputbox
            var value = this.newTodoItem && this.newTodoItem.trim();

            // Check if the input box is empty or not, perform logic
            if(value !== ''){
                // sending event to parent component newTodoItem value
                this.$emit('addTodo', value);
                // inputbox init
                this.clearInputbox();
            }
        },
        clearInputbox(){
            this.newTodoItem = '';
        }
    }
}
</script>