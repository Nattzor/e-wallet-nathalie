<template>
<main>
<div>
  <h1> E-Wallet</h1>
  <h5>Active card</h5>
  <CardCard class="activeCard" v-if="isActive" v-bind:card="isActive"/>
</div>
<div class="cardStack">
  <CardCard v-for="card in cards" :key ="card.id" v-bind:card="card" @activeCard="activeCard" />
  <button class="bottomOfPage" @click="changeView">Add new Card </button>
  </div>
  </main>
</template>

<script>
import CardCard from './CardCard.vue'

export default {
    data(){ return {
        isActive: null
    }
    },
    components: {CardCard},
    props: ['cards'],
    methods: {
        changeView() {
        this.$emit('viewChange');
    }, 
activeCard(card) {
this.isActive = card
this.$emit('activeCard', this.isActive)
}
    },
}
</script>


<style scoped>
.activeCard{
    margin-bottom: 3rem;
    margin-top: 0rem;
}
.cardStack{
display: grid;
grid-auto-rows: 2rem;
background-color: rgb(241, 233, 232);
font-family: 'PT Mono'
}

.bottomOfPage {
position: relative;
width: 382px;
height: 80px;
top: 15rem;
}
</style>