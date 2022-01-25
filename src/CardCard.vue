<template>
  <div :class="{ active: isActive }" @click="isActive = !isActive" class="wrapper" v-bind:style="cardColors"> 
      <h1>{{card.cardnum}}</h1>
      <img class="logo" v-bind:src="card.vendor.logo">
      <p class="name">Cardholder name: <br>{{card.name}}</p>
       <p class="date">Year/Month <br>{{card.year}}/{{card.month}}</p>
       
  </div>
</template>

<script >
export default {
    data() { return {
        isActive: "false"
    }
    },
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
    position: relative;
width: 382px;
height: 241px;
left: 16px;
top: 138px;

filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
}
.wrapper:nth-child(2){
    position: relative;
width: 382px;
height: 241px;
left: 16px;
top: 466px;
}

.wrapper:nth-child(3){
    position: relative;
width: 382px;
height: 241px;
left: 16px;
top: 515px;
}

.name {
  margin-left: 1rem;
}
.date {
  text-align: right;
  margin: 1rem;
}
</style>
