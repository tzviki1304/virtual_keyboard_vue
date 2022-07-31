<template>
    <main>
        <h1>parent</h1>
        <div class="main" >    
            <div class="com-1" ><component1 /></div>
            <div class="com-2" ><component2 /></div>
        </div>
    </main>
</template>

<script>
    import component1 from "./component_1";
    import component2 from "./component_2";

    export default {

        components: {
            component1,
            component2
        },
    }
</script>

<style  scoped>
main{
    height: 400px;
    border: 1px solid #4e6831;
}
.main{
    position: absolute;
    width: 100%; height: 300px;
    display: flex;
    align-items: flex-start;
    flex-direction: row;
    justify-content: space-around;
    flex-wrap: nowrap;
    align-content: center;
}
.com-1{
    /* position: absolute;
    left: 0px; top: 60px;*/
    width: 550px; height: 250px;
    margin: 20px; 
    border: 1px solid red;
}
.com-2{
    /* position: absolute;
    right: 0px; top: 60px;*/
    width: 550px; height: 250px;
    margin: 20px; 
    border: 1px solid blue;
}
</style>