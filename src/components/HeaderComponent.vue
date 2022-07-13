<template>
    <header>
        <input type="text" v-model="userInput" @keyup="$emit('userSearch', userInput)">
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data(){
        return{
            userInput: '',
        }
    },
}
</script>

<style lang="scss">
    
</style>