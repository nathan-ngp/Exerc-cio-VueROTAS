<template>
  <div id="infracoes">
      <div v-for="(infracao, index) in placa" :key="index">
          <input type="datetime" :value="infracao.DADOS_INFRACAO.DATAHORA">
          <input type="text" :value="infracao.LOCALIDADE">
          <input type="text" :value="infracao.DADOS_INFRACAO.TIPO">
          <input type="number" :value="infracao.DADOS_INFRACAO.VALOR">
          <button @click="novaConsulta">Nova Consulta</button>
          <span v-if="infracao.DADOS_INFRACAO.TIPO == 'VELOCIDADE'" id="spanVelocidadeMaxima">Velocidade Máxima: {{infracao.DADOS_INFRACAO.VEL_MAXIMA}}</span>
      </div>
  </div>
</template>

<script>
export default {
    data:function(){
        return{
        }
    },
    computed:{
        placa:function(){
            return this.$store.state.infracoesVeiculo
        } 
    },
    methods: {
        novaConsulta:function(){
            this.$router.push('/')
        },
        }
    }
</script>

<style>
    #infracoes{
        display: block;
        padding: 20px;
    }

    #infracoes input{
        padding: 10px;
        margin-left: 20px;
    }

    #infracoes button{
        padding: 10px;
        margin-left: 20px;
    }

    #dados{
        background-color: black;
    }

    #spanVelocidadeMaxima{
        color: red;
    }
</style>