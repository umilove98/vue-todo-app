<template>
    <section>
        <ul class="list-group list-group-flush">
            <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="list-group-item">
                {{ todoItem }}
                <b-button v-on:click="removeTodo(todoItem, index)" variant="danger" class="float-right" >remove</b-button>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    props: ['propsdata'],
    methods: {
    	removeTodo(todoItem, index){
            this.$emit('removeTodo', todoItem, index);
        }
    }    
}
</script>