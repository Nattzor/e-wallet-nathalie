<template>
    <main class="app">
      <nav>
        <a @click="currentView = 'wallet'"> </a> 
        </nav>
        <div>
          <Wallet v-bind:cards="cards"  v-if="currentView == 'wallet'"/>
            <AddCard v-else-if="currentView == 'addCard'"/>

          <button @click="currentView = 'addCard'">Add new Card </button>
          </div>
    
  </main>
</template>

<script>
import Wallet from './Wallet.vue'
import AddCard from './AddCard.vue'

export default {
  components: {Wallet, AddCard},
data() { return {
  cards: [{id: 0, fname: 'Nathalie', lnam: 'Larsson', cardnum: 666-666-666,}],
currentView: 'wallet'
}
}
}
</script>

<style>

</style>