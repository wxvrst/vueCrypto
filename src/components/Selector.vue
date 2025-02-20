<script>
    export default {
        props: {
            setCrypto: {
                type: Function,
                required:true,
            },
            cryptoNow: {
                type: String,
                required:true,
            },
        },
    }
</script>

<template>
    <ul>
        <li @click="setCrypto('BTC')"  :class="cryptoNow=== 'BTC' ? 'active' : ''">Bitcoin</li>
        <li @click="setCrypto('ETH')"  :class="cryptoNow=== 'ETH' ? 'active' : ''">ETH</li>
        <li @click="setCrypto('USDT')"  :class="cryptoNow=== 'USDT' ? 'active' : ''">USDT</li>
    </ul>
</template>

<style scoped>
    ul {
        list-style: none;
        width: 200px;
        padding: 0;
        border-radius: 4px;
        border:3px solid black;
    }
    
    li {
        display:block;
        background:#1A032D;
        color:white;
        padding:20px 0;
    }
    
    li:hover, li.active {
        background:#24043E;
        cursor:pointer;
    }
</style>