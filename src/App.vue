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
  cards: [{id: 0, fname: 'Nathalie', lname: 'Larsson', cardnum: 666666666, year: 22, month:21, ccv: 555},
    {id: 1, fname: 'Nathalie', lname: 'Larsson', cardnum: 3333333333, year: 22, month:21, ccv: 555},
    {id: 2, fname: 'Nathalie', lname: 'Larsson', cardnum: 9999999999, year: 22, month:21, ccv: 555}],
currentView: 'wallet'
}
}
}
</script>

<style>

</style>