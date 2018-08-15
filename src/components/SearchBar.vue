<template>
    <input @input="onInput" type="text"/>
</template>


<script>
    export default {
        name: 'SearchBar',
        methods: {
            onInput: function(e) {
               this.$emit('termChange', e.target.value);
            }
        }
    }
</script>


<style <style scoped>
    input {
        width: 75%
    }

    div {
        text-align: center
    }
</style>
