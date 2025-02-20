<script>
    export default {
        props: {
            changeAmount: {
                type:Function,
                required:true,
            },
            convert: {
                type:Function,
                required:true,
            },
            favourite: {
                type:Function,
                required:true,
            },
        },
    }
</script>

<template>
    <input type="number" @input="changeAmount($event.target.value)" placeholder="Enter the number" min="0"><br>
    <button @click="convert()">Convert</button>
    <button @click="favourite()">In favourites </button>
</template>

<style scoped>
    input{
        border-radius: 4px;
        border:none;
        padding: 12px 16px;
        font-size: 1.2em;
        background: #fafafa;
        color:#333333;
        width:500px;
        margin-bottom: 24px;
    }
    button{
        margin-right: 12px;
        padding:12px 16px;
        color:white;
        width:160px;
        text-transform: uppercase;
        cursor: pointer;
        background:#1A032D;
        margin-bottom: 24px;
        border:none;
        border-radius: 4px;
        transition: transform .2s ease;
    }
    button:hover{
        transform: scale(1.06) translateY(-1px);
    }
</style>