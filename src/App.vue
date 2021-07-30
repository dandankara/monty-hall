<template>
  <div id="app">
    <h1>Monty Hall Problem</h1>

    <div class="form">

      <div v-if="!started">
        <label for="portsAmount">Quantas portas?</label>
        <input type="text" id="portsAmount" size="3"
          v-model.number="portsAmount"> 
      </div>  

      <div v-if="!started">
        <label for="selectedPort">Qual a porta premiada?</label>
        <input type="text" id="selectedPort" size="3"
          v-model.number="selectedPort">
      </div>

      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
      
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" v-bind:key="i">
        <Door :hasGift="i === selectedPort" :number="i" />
      </div>  
    </div> 
  </div>
</template>

<script>
import Door from './components/Door';

export default {
  name: 'App',
  components: {
    Door
  },
  data: function() {
    return {
      started:false,
      portsAmount: 3, //Padrão de portas no começo
      selectedPort: null
    }
  }
  
}

</script>

<style>

  * {
    box-sizing: border-box;
    
  }

  body{
    background: #606c88;  /* fallback for old browsers */
    background: -webkit-linear-gradient(to right, #3f4c6b, #606c88);  /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(to right, #3f4c6b, #606c88); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  }

  #app{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #app h1 {
    border: 1px solid #000;
    background-color: #0004;
    padding: 1.2rem;
    margin-bottom: 2.5rem;
  }

  .form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 1rem;
  }

  .doors{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-self: center;

  }

</style>