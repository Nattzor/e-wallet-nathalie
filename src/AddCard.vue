<template>
<main>
  <h1>ADD A NEW BANK CARD</h1>
  <form @submit.prevent="sendCard">
      <label for="cardNumber">CARD NUMBER</label><br>
      <input v-model="cardInfo.cardNumber" type="text" id="cardNumber"><br>
      <label for="cardHolder">CARDHOLDER NAME</label><br>
      <input v-model="cardInfo.name" type="text" id="cardHolder" placeholder="FIRSTNAME LASTNAME"><br>
          <label for="month">MONTH</label>
          <select name="month" v-model="cardInfo.month">
            <option v-for="month in months" :key="month" value:value="month">
              {{ month }}
            </option>
          </select>
          <label for="year">YEAR</label>
          <select name="year" v-model="cardInfo.year">
            <option v-for="year in years" :key="year" name="year">
              {{ year }}
            </option>
          </select>

      <label for="vendor">VENDOR</label>
      <select id="vendor" name="vendor" v-model="cardInfo.vendor">
        <option v-for="vendor in vendor" :key="vendor.name" :name="vendor" :value="vendor"
        >
          {{ vendor.name }}
        </option>
      </select>
       <label for="cardCcv">CCV</label><br>
      <input v-model="cardInfo.ccv" type="text" id="cardCcv"><br>
        <button class="buttonOnBottom"> Add CARD</button>
       </form>
  </main>
</template>

<script>
export default {
    data() { return {
        cardInfo: { cardNumber: "", name: "", date: "", ccv:""
        },  months: [
        '01',
        '02',
        '03',
        '04',
        '05',
        '06',
        '07',
        '08',
        '09',
        '10',
        '11',
        '12',
      ],
      years: ['2022', '2023', '2024', '2025', '2026'],
      vendor: [
        {
          name: 'Bitcoin Inc',
          backgroundColor: '#FFAE34',
          color: 'black',
          logo: require('./assets/bitcoin.svg'),
        },
        {
          name: 'Ninja Bank',
          backgroundColor: '#222222',
          color: 'white',
          logo: require('./assets/ninja.svg'),
        },
        {
          name: 'Block Chain Inc',
          backgroundColor: '#8B58F9',
          color: 'white',
          logo: require('./assets/blockchain.svg'),
        },
        {
          name: 'Evil Corp',
          backgroundColor: '#F33355',
          color: 'white',
          logo: require('./assets/evil.svg'),
        },
      ],
    }
    },
    methods: {
        sendCard(){
            this.$emit('sendCard', {...this.cardInfo})
              this.$emit('viewChange');
        }, 
    }
  }
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: auto;
}
form > * {
  margin: 0.25rem;
  font-size: 1rem;
}

</style>
