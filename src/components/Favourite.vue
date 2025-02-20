<script>
    export default {
        props: {
            favs: {
                type: Array,
                required: true,
            },
            getFromFavs: {
                type: Function,
                required: true,
            }
        },
    }
</script>

<template>
    <h2>Variants in favourite</h2>
    <div @click="getFromFavs(index)" v-for="(el,index) in favs" :key="index">
        <span>{{ el.from }}</span>
        <span>{{ el.to }}</span>
    </div>
</template>

<style scoped>
    h2 {
        color:white;
    }
    
    div {
        display: flex;
        justify-content: space-between;
        width:360px;
        margin:12px auto;
        transition: all 500ms ease;
    }
    
    div:hover {
        opacity:0.6;
        transform: scale(1.05);
        cursor: pointer;
    }
    
    span {
        padding: 12px 16px;
        background:#8C00FF;
        color:white;
    }
    
</style>