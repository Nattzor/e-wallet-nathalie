<template>
    <main class="app">
      <nav>
        <a @click="currentView = 'home'"> </a> 
        </nav>
        <div>
          <Wallet v-if="currentView == 'home'"/>
            <AddCard v-else-if="currentView == 'about'"/>

          <button @click="currentView = 'about'">Add new Card </button>
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
currentView: 'home'
}
}
}
</script>

<style>

</style>