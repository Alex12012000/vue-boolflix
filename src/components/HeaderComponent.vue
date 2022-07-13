<template>
    <header>
        <div class="logo">
            <img src="../assets/504e88f1a30f968e13f4cdd854aab685.png" alt="">
        </div>
        <div class="search-bar">
            <input type="text" v-model="userInput" @keyup="$emit('userSearch', userInput)">
            <button @click="$emit('filmCall'), $emit('tvCall')">Search</button>
        </div>
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
    props: {
        filmCall: Function,
        tvCall: Function
    },
}
</script>

<style lang="scss" scoped>

header {
    height: 90px;
    padding: 0 20px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
    .logo {
        width: 200px;
    }

    .search-bar {
        input {
            margin: 0 10px;
            padding: 5px 10px;
            border-radius: 20px;
            border: 1px solid red;
            background-color: rgb(17, 17, 17);
            color: white;
        }

        button {
            padding: 5px 10px;
            border-radius: 10px;
            border: 1px solid red;
            background-color: rgb(17, 17, 17);
            color: white;
            cursor: pointer;
        }
    }
}

</style>