<template>
    <b-container fluid style="padding:50px;">
    <div id="app">
        <TodoHeader></TodoHeader>
        <TodoInput v-on:addTodo="addTodo"></TodoInput>
        <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
        <TodoFooter v-on:removeAll="clearAll" v-bind:totalItems="totalItems"></TodoFooter>
    </div>
    </b-container>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

export default {
    data(){
        return {
            todoItems: [],
            totalItems: 0
        }
    },
    created(){
      //  create TodoList
        if(localStorage.length > 0){
            for(var i = 0; i < localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
        this.totalItems = localStorage.length;

    },
    methods: {
        addTodo(todoItem){
            // add data to localStorage
            localStorage.setItem(todoItem, todoItem);
            this.todoItems.push(todoItem);
            this.totalItems++;
        },
        removeTodo(todoItem, index){
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        },
        clearAll(){
            // remove all data on localStorage and todoItems init
            localStorage.clear();
            this.todoItems = [];
        }
    },    
    components: {
        'TodoHeader': TodoHeader,
        'TodoInput': TodoInput,
        'TodoList': TodoList,
        'TodoFooter': TodoFooter
    }
}
</script>