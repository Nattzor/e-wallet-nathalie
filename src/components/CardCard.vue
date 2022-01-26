<template>
  <div class="wrapper" v-bind:style="cardColors" @click="$emit('activeCard', card)"> 
    <h1>{{card.cardNum}}</h1>
    <div class="logoWifi">
    <img :src="card.vendor.wifi">
    <img :src="card.vendor.logo">
    </div>
    <img class="chip" :src="card.vendor.chip">
    <div class="nameAndDate">
    <p class="name">Cardholder name: <br>{{card.name}} </p>
    <p class="date">Year/Month <br>{{card.year}}/{{card.month}}</p>
    </div>
</div>
</template>

<script >
export default {
props: ['card'],
computed: {
    cardColors() {
      return {
        backgroundColor: this.card.vendor.backgroundColor,
        color: this.card.vendor.color,
    }
},
},
    }

</script>

<style scoped>
img {
text-align: left;
}

.wrapper {
width: 382px;
height: 241px; 
filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
border-radius: 2%;
}

.logoWifi {
  display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 height: 4rem;
}

.chip {
  margin-top: 2rem;
}

.nameAndDate {
  display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 margin-top: 3rem;
}

</style>
