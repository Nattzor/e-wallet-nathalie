<template>
  <div class="wrapper"> 
      <h1>{{card.cardnum}}</h1>
      <p>Cardholder name: <br>{{card.fname}} {{card.lname}} </p>
       <p>Year/Month <br>{{card.year}}/{{card.month}}</p>
  </div>
</template>

<script>
export default {
props: ['card'],
}
</script>

<style>

.warpper {
position: absolute;
width: 382px;
height: 241px;
left: 16px;
top: 138px;

filter: drop-shadow(0px 0px 32px rgba(0, 0, 0, 0.1));
}

</style>