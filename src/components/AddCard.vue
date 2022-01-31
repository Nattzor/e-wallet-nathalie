<template>
<main>
    <div>
  <h1>ADD A NEW BANK CARD</h1>
  <p v-for="error in errors" :key="error">
    <b class="error" v-if="errors.length"> {{errors}} </b> </p>
<div class="wrapper" v-bind:style="cardColors">
    <div class="logoWifi">
    <img :src="cardInfo.vendor.wifi">
    <img :src="cardInfo.vendor.logo">
    </div>
     <img class="chip" :src="cardInfo.vendor.chip">
     <h1>{{seperateCardNum}}</h1>
    <div class="nameAndDate">
    <p class="name">Cardholder name: <br>{{cardInfo.name}} </p>
    <p class="date">Year/Month <br>{{cardInfo.month}}/{{cardInfo.year}}</p>
    </div>
</div>

  <form  @submit.prevent="sendCard">
      <label for="cardNum">CARD NUMBER</label><br>
      <input v-model="cardInfo.cardNum" type="text" id="cardNum" maxlength="16"><br>
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
      <input v-model="cardInfo.ccv" type="text" id="cardCcv" maxlength="3"><br>
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
          backgroundColor: '#D0D0D0',
          color: 'black',
          logo: require('../assets/bitcoin.svg'),
          wifi: require('../assets/wifi_white.svg'),
          chip: require('../assets/chip.svg')
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
          wifi: require('../assets/wifi_white.svg'),
          chip: require('../assets/chip.svg')
        },
        {
          name: 'Ninja Bank',
          backgroundColor: '#222222',
          color: 'white',
          logo: require('../assets/ninja.svg'),
          wifi: require('../assets/wifi_white.svg'),
          chip: require('../assets/chip.svg')
        },
        {
          name: 'Block Chain Inc',
          backgroundColor: '#8B58F9',
          color: 'white',
          logo: require('../assets/blockchain.svg'),
          wifi: require('../assets/wifi.svg'),
          chip: require('../assets/chip.svg')
          
        },
        {
          name: 'Evil Corp',
          backgroundColor: '#F33355',
          color: 'white',
          logo: require('../assets/evil.svg'),
          wifi: require('../assets/wifi_white.svg'),
          chip: require('../assets/chip.svg')
        },
      ],
       errors: [],
    }
    },
    computed: {
    cardColors() {
      return {
        backgroundColor: this.cardInfo.vendor.backgroundColor,
        color: this.cardInfo.vendor.color,
    };
},  seperateCardNum() {
      let output = ""
         for( let i = 0; i < this.cardInfo.cardNum.length; i++) {
         if  ( (i+1) % 4 == 0) {
           output += this.cardInfo.cardNum[i] + ' '; 
       } else { output += this.cardInfo.cardNum[i];
       }
    } return output
},
    },
    methods: {
        sendCard(){
          this.validate()
          if (this.errors.length == 0) {
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
            this.errors.push('name required')
          } 
        } 
    }
}
</script>

<style scoped>
.wrapper {
  width: 382px;
height: 241px; 
border-radius: 2%;
filter: drop-shadow(0px 0px 16px rgba(0, 0, 0, 0.12));
}

h1 {
  margin: 0.5rem;
}

.logoWifi {
  display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 height: 4rem;
}

.nameAndDate {
  display: flex;
 flex-direction: row;
 width: 100%;
 justify-content: space-between;
 height: 4rem;
 font-family: 'PT Mono'
}

.chip {
  margin-left: 0.5rem;
}

.name {
  margin-left: 0.5rem;
}

.date {
  margin-right: 0.5rem;
}

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
.buttonOnBottom {
  background-color: black;
  color: white;
}

.error {
  color: red;
}

</style>
