<template>
    <h1>component 2</h1>
    <div>
        <input type="text" v-model="usernName" placeholder="user name" >
        <input type="text" v-model="numberPhone" placeholder="number phone" >
        <textarea v-model="note" cols="31" rows="3" placeholder="test sum note"></textarea>
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
                usernName: '770',
                numberPhone: '',
                note: '',
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