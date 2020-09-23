<template>
  <section @input="addCard" class="card-form">
    <label for="number" class="col-2">Card Number:</label>
    <input
      name="number"
      type="text"
      v-model="newCard.cardnumber"
      maxlength="16"
      class="col-2"
      placeholder="XXXX-XXXX-XXXX-XXXX"
    />
    <label for="cardholder" class="col-2"> FULL NAME</label>
    <input
      type="text"
      name="cardholder"
      v-model="newCard.cardholder"
      placeholder="FIRSTNAME LASTNAME"
      class="col-2"
    />
    <label for="month" class="col-2">VALID THRU MONTH</label>
    <select id="month" name="month" v-model="newCard.expmonth" class="col-2">
      <option value="01">01</option>
      <option value="02">02</option>
      <option value="03">03</option>
      <option value="04">04</option>
      <option value="05">05</option>
      <option value="06">06</option>
      <option value="07">07</option>
      <option value="08">08</option>
      <option value="09">09</option>
      <option value="10">10</option>
      <option value="11">11</option>
      <option value="12">12</option>
    </select>
    <label for="year" class="col-2">VALID THRU YEAR</label>
    <select id="year" name="year" v-model="newCard.expyear" class="col-2">
      <option value="21">21</option>
      <option value="22">22</option>
      <option value="23">23</option>
      <option value="24">24</option>
      <option value="25">25</option>
    </select>
    <label for="vendor" class="col-2">Choose vendor</label>
    <select id="vendor" name="vendor" v-model="newCard.vendor" class="col-2">
      <option value="bitcoin">Bitcoin</option>
      <option value="blockchain">Blockchain</option>
      <option value="evil">Evil</option>
      <option value="ninja">Ninja</option>
    </select>
    <label for="ccv" class="col-2">CCV</label>
    <input type="number" name="ccv" v-model="newCard.ccv" maxlength="3" class="col-2" />
    <a href="#" class="col-2" @click="addCard">Add new card!</a>
  </section>
</template>
<script>
export default {
    name: "CardForm",
    data () {
      return {
        newCard: {
          id: "", cardnumber: "", cardholder: "", expyear: "", expmonth: ""
        }
      }
    },
    methods: {
      addCard(event) {
        this.$emit('addCard', {card: this.newCard, id: this.newCard.id, event: event});  
      }
      
    }
    
}
</script>
<style scoped>
.card-form {
  margin: 2rem 0 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0 1rem;
}

.col-2 {
  grid-column: auto/span 2;
}

.card-form label {
  padding: 0.25rem 0;
  font-size: 0.7rem;
  text-transform: uppercase;
}

.col-1 {
  grid-column: auto/span 1;
}

.card-form input,
select {
  border: 1px solid #000;
  border-radius: 0.25rem;
  padding: 0.5rem;
  height: 2.6rem;
  margin: 0 auto;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  font-size: 1rem;
  width: 40%;
}

a {
  
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  height: 4rem;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 700;
  text-decoration: none;
  color: #000;
  border: 0.125rem solid #000;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: 0.5rem;
  padding: 0.5rem;
  margin: 1rem auto;
}
</style>