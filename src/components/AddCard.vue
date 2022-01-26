<template>
<main>
    <div>
  <h1>ADD A NEW BANK CARD</h1>
  <p v-for="error in errors" :key="error">
    <b v-if="errors.length"> {{errors}} </b> </p>
<div v-bind:style="cardColors">
    <h1>{{seperateCardNum}}</h1>
    <!-- <div class="logoWifi"> -->
    <!-- <img :src="cardInfo.vendor.wifi"> -->
    <img :src="cardInfo.vendor.logo">
    <!-- </div> -->
    <!-- <img class="chip" :src="cardInfo.vendor.chip"> -->
    <p class="name">Cardholder name: <br>{{cardInfo.name}} </p>
    <p class="date">Year/Month <br>{{cardInfo.month}}/{{cardInfo.year}}</p>
</div>

  <form @:submit.prevent="validate" @submit.prevent="sendCard">
      <label for="cardNum">CARD NUMBER</label><br>
      <input v-model="cardInfo.cardNum" type="text" id="cardNum"><br>
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
        <option v-for="vendor in vendor" :key="vendor.name" :name="vendor" :value="vendor">
          {{ vendor.name }}
        </option>
      </select>
       <label for="cardCcv">CCV</label><br>
      <input v-model="cardInfo.ccv" type="text" id="cardCcv"><br>
        <button class="buttonOnBottom"> Add CARD</button>
       </form>
       </div>
  </main>
</template>

<script>
export default {
    data() { return {
        cardInfo: { cardNum: "", name: "", date: "", ccv:"", vendor: {
          name: 'Bitcoin Inc',
          backgroundColor: '#FFAE34',
          color: 'black',
          logo: require('../assets/bitcoin.svg'),
        }
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
      years: ['2022', '2023', '2024', '2025', '2026', '2027'],
      vendor: [
        {
          name: 'Bitcoin Inc',
          backgroundColor: '#FFAE34',
          color: 'black',
          logo: require('../assets/bitcoin.svg'),
        },
        {
          name: 'Ninja Bank',
          backgroundColor: '#222222',
          color: 'white',
          logo: require('../assets/ninja.svg'),
        },
        {
          name: 'Block Chain Inc',
          backgroundColor: '#8B58F9',
          color: 'white',
          logo: require('../assets/blockchain.svg'),
        },
        {
          name: 'Evil Corp',
          backgroundColor: '#F33355',
          color: 'white',
          logo: require('../assets/evil.svg'),
        },
      ],
       errors: null,
    }
    },
    computed: {
    cardColors() {
      return {
        backgroundColor: this.vendor.backgroundColor,
        color: this.vendor.color,
    };
},  seperateCardNum() {
      let output = ""
         for( let i = 0; i < this.cardInfo.cardNum.length; i++) {
         if  ( (i+1) %4 == 0) {
           output = this.cardInfo.cardNum[i] + ' ';
         
       }
    } return output
},
    },
    methods: {
        sendCard(){
          if (this.errors == null) {
            this.$emit('sendCard', {...this.cardInfo})
              this.$emit('viewChange');
          }
        }, 
        // != /(\d{16}|\d{4}[- ]\d{4}[- ]\d{4}[- ]\d{4}")/g) 
        validate() {
          if (this.cardInfo.cardNum.length != 16) {
        this.errors.push('must contain 16 digits')
          }
          if (this.cardInfo.name.length == 0) {
            this.errors.push('must contain lest 1 letter')
          }
        }
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
