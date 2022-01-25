<template>
<main>
<div>
  <h1> E-Wallet</h1>
  <h5>Active card</h5>
  <CardCard v-if="isActive" v-bind:card="isActive"/>

  <CardCard v-for="card in cards" :key ="card.id" v-bind:card="card" @activeCard="activeCard" />
  </div>
  <button class="bottomOfPage" @click="changeView">Add new Card </button>
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
    // computed: {
    // cardColors() {
    //   return {
    //     backgroundColor: this.card.vendor.backgroundColor,
    //     color: this.card.vendor.color,
    //   };
    // }
    // }
}
</script>


<style>
div{
  width: 382px;
  background-color: rgb(241, 233, 232);
}

.bottomOfPage {
  position: relative;
width: 382px;
height: 80px;
left: 16px;
top: 2rem;
}
article{
    margin-bottom: 10rem;;
}
</style>