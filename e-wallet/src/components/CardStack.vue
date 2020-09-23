<template>
  <section id="cardStack">
    <Card
      v-for="card in cards"
      :key="card.id"
      :cardInfo="card"
      @removeCard="removeCard"
      @click.native="showCard(card.id)"
    ></Card>
  </section>
</template>
<script>
import Card from '../components/Card.vue'
export default {
  name: "CardStack",
  props: {
    cards: Array
  },
  data () {
    return {
  }
},
    components: {
      Card
    },
    methods: {
      showCard(id) {
        let cardInfo = this.$props.cards.find((card) => card.id == id) 
        this.$emit('showCard', cardInfo)
      },
      removeCard(payload) {
      this.$emit('removeCard', payload)
    }
    }
}
</script>
<style scoped>
#cardStack {
  margin: 2rem 0 12rem;
  display: grid;
  grid-auto-rows: 4rem;
}
</style>