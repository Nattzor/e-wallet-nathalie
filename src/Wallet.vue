<template>
<main>
<div>
  <h1> E-Wallet</h1>
  <h3>Active card</h3>
  <CardCard v-for="card in cards" :key ="card.id" v-bind:card="card" />
  </div>
  <button class="bottomOfPage" @click="changeView">Add new Card </button>
  </main>
</template>

<script>
import CardCard from './CardCard.vue'

export default {
    components: {CardCard},
    props: ['cards'],
    methods: {
        changeView() {
        this.$emit('viewChange');
    }
    }
}
</script>


<style>
div{
  height: 337px;
  width: 382px;
  background-color: rgb(241, 233, 232);
}
.bottomOfPage {
  position: relative;
width: 382px;
height: 80px;
left: 16px;
top: 799px;
}
</style>