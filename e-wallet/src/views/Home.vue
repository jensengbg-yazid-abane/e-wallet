<template>
  <div class="home">
    <Top :topMessage="topMessage" :activeCard="activeCard" />
    <Card :cardInfo="cardInfo" @removeCard="removeCard" :activeCard="activeCard" />
    <button class="remove" v-if="this.cardInfo.id" @click="showAlert">Remove Card</button>
    <RemoveAlert :show="show" @result="alertResult" />
    <CardStack :cards="cards" @showCard="showCard" />
    <router-link  class = "add" to="/AddCard">ADD A NEW CARD</router-link>
  </div>
</template>

<script>
import Top from '../components/Top.vue'
import Card from '../components/Card.vue'
import CardStack from '../components/CardStack.vue'
import RemoveAlert from '../components/RemoveAlert.vue'

export default {
  name: 'Home',
  data () {
    return {
      topMessage: "E-Wallet",
      activeCard: true,
      deleteResponse: false,
      show: false,
      cardInfo: {
          
        }
    }
  },
  components: {
    Top,
    Card, 
    CardStack,
    RemoveAlert
  },
  props: {
    cards: Array
  },
  methods: {
    showCard(payload) {
      this.cardInfo = payload;
    },
    removeCard(payload) {
      this.$emit('removeCard', payload)
    },
    alertResult(payload) {
    this.show = false
    if(payload == true) {
      this.$emit('removeCard', this.cardInfo.id)
    }
  },
    showAlert() {
    this.show = true;
    }
}
}
</script>
<style scoped>
.add {
  color: #000;
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid black;
  padding: 10px 20px;
  border-radius: 5px;
  margin-bottom: 300px;
}
.remove {
  margin-top: 1%;
  color: #000;
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid black;
  padding: 10px 20px;
  border-radius: 5px;
   
}
</style>
