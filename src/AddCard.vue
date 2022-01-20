<template>
<main>
  <h1>ADD A NEW BANK CARD</h1>
  <form @submit.prevent="sendCard">
      <label for="cardNumber">CARD NUMBER</label><br>
      <input v-model="cardInfo.cardNumber" type="text" id="cardNumber"><br>
      <label for="cardHolder">CARDHOLDER NAME</label><br>
      <input v-model="cardInfo.fname" type="text" id="cardHolder" placeholder="FIRSTNAME LASTNAME"><br>
       <label for="cardDate">YEAR/MONTH</label><br>
      <input v-model="cardInfo.date" type="text" id="cardDate"><br>
       <label for="cardCcv">CCV</label><br>
      <input v-model="cardInfo.ccv" type="text" id="cardCcv">
       </form>
  </main>
</template>

<script>
export default {
    data() { return {
        cardInfo: { cardNumber: "", fname: "", lname: "", date: "", ccv:""
        }
    }
    },
    methods: {
        sendCard(){
            this.$emit('send', {...this.cardInfo})
        }
    }

}
</script>

<style>

</style>