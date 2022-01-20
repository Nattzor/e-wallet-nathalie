<template>
<div>
  <h1> E-Wallet</h1>
  <CardCard v-for="card in cards" :key ="card.id" v-bind:card="card" />
  </div>
</template>

<script>
import CardCard from './CardCard.vue'

export default {
    components: {CardCard},
    props: ['cards'],

}
</script>

<style>

</style>