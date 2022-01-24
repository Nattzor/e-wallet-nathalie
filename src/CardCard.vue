<template>
  <div class="wrapper"> 
      <h1>{{card.cardnum}}</h1>
      <p class="name">Cardholder name: <br>{{card.name}}</p>
       <p class="date">Year/Month <br>{{card.year}}/{{card.month}}</p>
  </div>
</template>

<script >
export default {
props: ['card'],
}
</script>

<style scoped>
.name {
  margin-left: 15px;
}
.valid-thru {
  margin-right: 15px;
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

<style scoped>

.wrapper {
    position: absolute;
width: 382px;
height: 241px;
top: 138px;
}
.wrapper:nth-child(2) {
    position: absolute;
width: 382px;
height: 241px;
top: 419px;

background-color: rgb(113, 113, 122);
filter: drop-shadow(0px 0px 32px rgba(0, 0, 0, 0.1));
}
.wrapper:nth-child(3) {
    position: absolute;
width: 382px;
height: 241px;
top: 466px;
background-color: rgb(32, 29, 29);
color: white;
filter: drop-shadow(0px 0px 32px rgba(0, 0, 0, 0.1));
}
/* .wrapper:nth-child(1){
    position: relative;
width: 382px;
height: 241px;
left: 16px;
top: 515px;

} */
.name {
    text-align: left;
}
.date {
    text-align: right;
}
.chip {
    text-align: left;
}

</style>