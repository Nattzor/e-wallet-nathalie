<template>
    <main class="app">
      <nav>
        <a @click="currentView = 'wallet'"> </a> 
        </nav>
        <div>
          <Wallet v-bind:cards="cards" v-if="currentView == 'wallet'" @viewChange="changeView" />
    <AddCard v-else @viewChange="changeView" @sendCard="newCardInfo"/>/>
             <button v-if="currentView == 'wallet'" @click="currentView = 'addCard'">Add new Card </button>
          </div>
  </main>
</template>

<script>
import Wallet from './Wallet.vue'
import AddCard from './AddCard.vue'

export default {
  components: {Wallet, AddCard},
data() { return {
  cards: [{id: 0, name: 'Nathalie Larsson', cardnum: 666+" "+666+" "+666, year: 22, month:21, ccv: 555, vendor: ''},
    {id: 1, name: 'Nathalie Larsson', cardnum: 333+" "+333+" "+3333, year: 22, month:21, ccv: 555, vendor: ''},
    {id: 2, name: 'Nathalie Larsson', cardnum: 999+" "+9999+" "+999, year: 22, month:21, ccv: 555, vendor: ''}],
currentView: 'wallet'
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
  height: 896px;
  width: 414px;
  text-transform: uppercase;
}
h1 {
  font-family: 'Source Sans Pro', sans-serif;
}
h4 {
  color: #222222;
  opacity: 60%;
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