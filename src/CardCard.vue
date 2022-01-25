<template>
  <div class="wrapper" v-bind:style="cardColors" @click="$emit('activeCard', card)"> 
      <div>
      <h1>{{card.cardnum}}</h1>
      <img class="logo" v-bind:src="card.vendor.logo">
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
      };
}
}
}
</script>

<style scoped>
img {
    text-align: left;
}

.wrapper {
    display: grid;
grid-auto-rows: 5rem;
filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
width: 382px;
height: 241px;
}

/* .wrapper:nth-child(3){
    position: relative;
width: 382px;
height: 241px;
left: 16px;
top: 515px;
} */

.logo {
 align-self: right;
}

.space {
    margin: 1rem;
}

.name {
  margin-left: 1rem;
}
.date {
  text-align: right;
  margin: 1rem;
}

.active {
   transform: translateY(-50px);
   transition: 1s;
}
</style>
