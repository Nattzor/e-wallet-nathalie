<template>
  <div :class="{ active: isActive }" @click="isActive = !isActive" class="wrapper" v-bind:style="cardColors"> 
      <h1>{{card.cardnum}}</h1>
      <img v-bind:src="card.vendor.logo">
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
// }, methods: {
// isActive() {
//    if (this.isActive !== 'true') {
//         this.isActive == 'true'
//       }
// }
}
}
}
</script>

<style scoped>
img {
    text-align: left;
}

.wrapper:nth-child() {
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
.cardheader {
  font-size: 10px;
  font-family: 'PT Mono', monospace;
  text-align: left;
}
.cardinfo {
  font-size: 15px;
  font-family: 'PT Mono', monospace;
  margin-top: 5px;
}
#cardnum {
  font-size: 23px;
  letter-spacing: 0.3rem;
  margin-top: 10px;
  font-family: 'PT Mono', monospace;
}
#wifiImg {
  max-width: 40px;
}
#chipImg {
  max-width: 40px;
}
.logos {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
  margin-left: 20px;
}
.upperpart {
  display: flex;
  justify-content: space-between;
}
.bottompart {
  display: flex;
  justify-content: space-between;
}
.card {
  background-color: #d0d0d0;
  border-radius: 5px;
  min-width: 350px;
  min-height: 200px;
  box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.81);
  margin-bottom: 40px;
}
</style>
