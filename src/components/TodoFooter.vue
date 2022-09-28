<template>
    <div>
        <div style="display:inline-block">
            <b-button v-on:click="clearTodo" variant="light">removeAll</b-button>
        </div>
        <div style="display:inline-block">complete : 0 / {{totalItems}}</div>
    </div>
</template>

<script>
export default {
    props: ['totalItems'],
    methods: {
        // remove all data on localStorage
        clearTodo(){
            this.$emit('removeAll');
        }
    }
    
}
</script>

<style>


</style>