<template>
  <div class="card" v-bind:style="cardColors" @click="$emit('activeCard', card)"> 
    <div class="logoWifi">
    <img :src="card.vendor.wifi">
    <img :src="card.vendor.logo">
    </div>
     <img class="chip" :src="card.vendor.chip">
     <h1>{{card.cardNum}}</h1>
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

.card {
width: 382px;
height: 241px; 
filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
border-radius: 2%;
}

h1 {
 text-align: center;
 margin: 0.5rem;
}

.logoWifi {
  display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 height: 4rem;
}

.chip {
  margin-top: 0.5rem;
  margin-left: 0.5rem;
}

.nameAndDate {
display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 margin-top: 1rem;
}

.name {
  margin-left: 0.5rem;
}

.date {
  margin-right: 0.5rem;
}

</style>
