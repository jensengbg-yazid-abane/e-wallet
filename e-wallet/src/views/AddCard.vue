<template>
  <div class="AddCard">
    <router-link class="back" to="/">MY CARDS</router-link>
    <Top :topMessage="topMessage" />
    <Card :cardInfo="cardInfo" />
    <CardForm v-bind:cards="cards" @addCard="addCard" />
  </div>
</template>
<script>
import Top from '../components/Top.vue'
import Card from '../components/Card.vue'
import CardForm from '../components/CardForm.vue'
export default {
    name: "AddCard",
    props: {
      cards: Array
    },
    components: {
      Top,
      Card,
      CardForm
    },
    data () {
      return {
        topMessage: "ADD A NEW BANK CARD",
        cardInfo: {
          id: "X", cardnumber: "XXXXXXXXXXXXXXXX", cardholder: "FIRSTNAME LASTNAME ", expyear: "YY", expmonth: "MM", ccv: "XXX", vendor: ""
        }
      }
    }, 
    methods: {
      addCard(payload) {
        this.cardInfo = payload.card;
        if(this.cardInfo.id == "") {
        this.cardInfo.id = this.$props.cards.length + 1;
        } 
        let checkExisting = this.$props.cards.find((cards) => cards.id == this.cardInfo.id)
        if(typeof(checkExisting) == 'undefined' && payload.event.type == 'click') {
          this.$emit('addCard', this.cardInfo)
          
        } 
    }
    }
}
</script>

<style scoped>
.AddCard {
    margin-top: 30px;

}
  .back {
  color: #000;
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid black;
  padding: 10px 20px;
  border-radius: 5px;
  }
</style>