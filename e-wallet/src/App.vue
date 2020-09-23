<template>
  <div id="app">   
    
    <router-view :cards="cards" @addCard="addCard" @removeCard="removeCard" />   
  </div>
</template>
<script>
export default {
  name: "App",
  data () {
       return {
         cards:
    [
      
    ]           
}}, 
  methods: {
  
   addCard(payload) {
    this.cards.push(payload);
  }, removeCard(id) {
    console.log(id);
    this.cards.splice(id - 1, 1)
    for(let i = 0; i < this.cards.length; i++) {
      this.cards[i].id = i + 1
      console.log(this.cards[i].id)
    } 
    location.reload();
  }
}, watch: {
  cards: {
    handler() { 
    console.log('Cards changed!');
    localStorage.setItem('cards', JSON.stringify(this.cards));
    },
    deep: true,
  },
}, mounted() {
  console.log('App mounted!');
  if (localStorage.getItem('cards')) {
    this.cards = JSON.parse(localStorage.getItem('cards'));
    }
},
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


</style>
