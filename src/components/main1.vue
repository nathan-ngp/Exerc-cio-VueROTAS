<template>
    <div id="main">
        <input type="text" placeholder="Placa" v-model="placaValidacao" maxlenght="8">
        <button @click="listaPlacas">Ok</button>
        <span id="span" v-if="existe">Placa não existente</span>
    </div>
</template>

<script>
const axios = require("axios");
export default {
data:function () {
    return{
        placaValidacao:'',
        existe:false
    }
},methods:{
    listaPlacas:function(){
        this.$store.state.infracoesVeiculo = this.$store.state.multas.filter(p => p.PLACA == this.placaValidacao,
        this.$router.push("/infracoes") 
        )
    }
}, mounted(){
    axios.get("http://localhost:8080/placas.json").then(p => this.$store.state.multas = p.data)
}
}
</script>

<style>
    #main input,button{
        margin-right: 20px;
        padding: 10px;
    }

    #span{
        width: 50px;
        height: 50px;
        color: red;
    }
</style>