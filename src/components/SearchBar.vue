<template>
    <div>
        <input type="text" v-model="userInput" @keyup="$emit('userSearch', userInput)">
    </div>
</template>
<script>
export default {
    name: 'SearchBar',
    data(){
        return{
            userInput: '',
        }
    }
}
</script>
<style lang="">
    
</style>