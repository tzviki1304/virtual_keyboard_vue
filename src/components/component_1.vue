<template>
    <h1>component 1</h1>
    <div>
        <input type="text" v-model="usernName" placeholder="user name" >
        <input type="text" v-model="numberPhone" placeholder="number phone" >
    </div>
    <h4>
        usernName : {{usernName}} <br>
        numberPhone :  {{numberPhone}}
    </h4>
</template>

<script>
    export default {
        data() {
            return {
                usernName: '',
                numberPhone: '',
            }
        },
    }
</script>

<style  scoped>
    div{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    input{
        width: 250px; height: 50px;
        font-size: 25px;
        border: none;
        border-bottom: 3px solid gray;
    }
    input:focus{
        outline: none;
    }
</style>