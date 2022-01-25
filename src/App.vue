<template>
    <main class="app">
      <nav>
        <a @click="currentView = 'wallet'"> </a> 
        </nav>
          <Wallet v-bind:cards="cards" v-if="currentView == 'wallet'" @viewChange="changeView" />
    <AddCard v-else @viewChange="changeView" @sendCard="newCardInfo"/>
  </main>
</template>

<script>
import Wallet from './components/Wallet.vue'
import AddCard from './components/AddCard.vue'

export default {
  components: {Wallet, AddCard},
data() { return {
  cards: [{id: 0, name: 'Nathalie Larsson', cardnum: 666+" "+666+" "+666, year: 22, month:21, ccv: 555, vendor: { 
          name: 'Ninja Bank',
          backgroundColor: '#222222',
          color: 'white',
          logo: require('./assets/ninja.svg'),
          wifi: require('./assets/wifi_white.svg'),
          chip: require('./assets/chip.svg')
        }},
    {id: 1, name: 'Nathalie Larsson', cardnum: 333+" "+333+" "+3333, year: 22, month:21, ccv: 555, vendor: {
          name: 'Block Chain Inc',
          backgroundColor: '#8B58F9',
          color: 'white',
          logo: require('./assets/blockchain.svg'),
          wifi: require('./assets/wifi_white.svg'),
          chip: require('./assets/chip.svg')
        }},
    {id: 2, name: 'Nathalie Larsson', cardnum: 999+" "+9999+" "+999, year: 22, month:21, ccv: 555, vendor:  {
          name: 'Evil Corp',
          backgroundColor: '#F33355',
          color: 'white',
          logo: require('./assets/evil.svg'),
          wifi: require('./assets/wifi_white.svg'),
          chip: require('./assets/chip.svg')
          
        }}],
currentView: 'wallet',
}
},
methods: {
  newCardInfo(newInfo) {
this.cards.push(newInfo) 
  }, 
    changeView() {
      if (this.currentView == 'wallet') {
        this.currentView = 'addCard';
      } else {
        this.currentView = 'wallet';
      }
    },
}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=PT+Mono&display=swap');

.app {
  display: flex;
  justify-content: center;
  margin: auto;
  width: 414px;
  text-transform: uppercase;
}
h1 {
  font-family: 'Source Sans Pro', sans-serif;
}
h5 {
  color: #222222;
  opacity: 60%;
  font-family: 'Source Sans Pro', sans-serif;
}
input {
  font-family: 'PT Mono', monospace;
}
button {
  font-family: 'PT Mono', monospace;
  font-size: 22px;
  width: 382px;
  height: 72px;
  border-radius: 8px;
}
</style>