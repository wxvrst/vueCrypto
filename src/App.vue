<script>
    import Input from './components/Input.vue';
    import Selector from './components/Selector.vue';
    import Favourite from './components/Favourite.vue';
    import CryptoConvert from 'crypto-convert';
    
    const convert = new CryptoConvert();
    
    export default {
        components: {
            Input,
            Selector,
            Favourite,
        },
        data() {
            return {
                amount:0,
                cryptoFrom:'',
                cryptoTo:'',
                error:'',
                result:0,
                favs:[],
            }
        },
        methods: {
            changeAmount(value){
                this.amount = value;
            },
            setCryptoFrom(val){
                this.cryptoFrom = val;
            },
            setCryptoTo(val){
                this.cryptoTo = val;
            },
            async convert(){
                if(this.amount<=0){
                    this.error='Enter the number more than 0';
                    return;
                }
                else if(this.cryptoFrom===''||this.cryptoTo===''){
                    this.error='Choose currency';
                    return;
                }
                else if(this.cryptoFrom===this.cryptoTo){
                    this.error='Choose another currency';
                    return;
                }
                
                this.error = '';
                
                await convert.ready();
                
                if(this.cryptoFrom==='BTC' && this.cryptoTo==='ETH') {
                    this.result = convert.BTC.ETH(this.amount);
                } else if(this.cryptoFrom==='BTC' && this.cryptoTo==='USDT') {
                    this.result = convert.BTC.USDT(this.amount);
                } else if(this.cryptoFrom==='ETH' && this.cryptoTo==='BTC') {
                    this.result = convert.ETH.BTC(this.amount);
                } else if(this.cryptoFrom==='ETH' && this.cryptoTo==='USDT') {
                    this.result = convert.ETH.USDT(this.amount);
                } else if(this.cryptoFrom==='USDT' && this.cryptoTo==='BTC') {
                    this.result = convert.USDT.BTC(this.amount);
                }else if(this.cryptoFrom==='USDT' && this.cryptoTo==='ETH') {
                    this.result = convert.USDT.ETH(this.amount);
                }
                
            },
            favourite(){
                this.favs.push({
                    from: this.cryptoFrom,
                    to: this.cryptoTo,
                });
            },
            getFromFavs(index){
                this.cryptoFrom = this.favs[index].from;
                this.cryptoTo = this.favs[index].to;
            },
        },
    }
</script>

<template>
    <h1>Crypto</h1>
    <Input :changeAmount="changeAmount" :convert="convert" :favourite="favourite"/>
    <p v-if="error">{{ error }}</p>
    <p v-if="result">{{ result }}</p>
    <Favourite :favs="favs" v-if="favs.length>0" :getFromFavs="getFromFavs"/>
    <div class="selectors">
        <Selector :setCrypto="setCryptoFrom" :cryptoNow="cryptoFrom"/>
        <Selector :setCrypto="setCryptoTo"  :cryptoNow="cryptoTo"/>
    </div>
</template>

<style scoped>
    .selectors{
        display: flex;
        justify-content: space-around;
        width:600px;
        margin:0 auto 120px auto;
    }
    p{
        font-family: "Orbitron", sans-serif;
        color:gold;
        margin-bottom:24px;
    }
</style>
