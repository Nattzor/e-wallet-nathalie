<template>
<div>
  <h1> Home </h1>
  <Card/>
  </div>
</template>

<script>
import Card from './CardCard.vue'

export default {
    components: {Card},
    props: ['cards'],

}
</script>

<style>

</style>