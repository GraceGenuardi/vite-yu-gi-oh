<template>
  <main class="main">

   


    <!-- Menù dropdown -->
    <div class="filter">
       <!-- INPUT PER RICERCARE LA CARTA IN BASE AL NOME -->
       <Filters @filter="fetchCards(filterName)" />

       <!-- ICONA -->
        <i class="fa-solid fa-magnifying-glass"></i>
    </div>

    <!-- FINE MENù -->

    <div class="container-main">

      <div class="found"><h3>Found 39 cards</h3></div>


      <ul class="cards">
        

        <Card v-for="card in cards" :key="card.id" :card="card" />

      </ul>
    </div>
    
  </main>

</template>

<script>
import axios from 'axios'
import Card from './Card.vue'
import Filters from './Filters.vue'


export default {
  components: {
    Card,
    Filters
  },
  data() {
    return {
      cards: [],
      filterName: ""
    }
  },
  methods: {
    fetchCards() {
  console.log('fetching data')
  const url = `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0&fname=${this.filterName}`;
  axios
    .get(url)
    .then((res) => {
      console.log(res)
      console.log(res.data)
      this.cards = res.data.data
    })
}
  },
  created() {
    this.fetchCards()
  },
}
</script>

<style lang="scss" scoped>
.main {
  padding: 50px 0;
  background-color: black;
}
.container-main{
  width: 1200px;
  margin-left: 350px;
}
.cards {
  display: grid;
  grid-template-columns: repeat(4,1fr);
  background-color: rgba(255, 255, 255, 0.586);
  padding: 50px;
}
.found{
  color: white;
  position: relative;
  width: 1075px;
  left: 70px;
  top: 75px;
  background-color: rgb(47, 47, 47);
  text-align: left;
  padding: 10px;
  
}
/**MENU RULES */
.filter {
  background-color: rgb(255, 104, 10);
  margin-bottom: 25px;
  display: flex;
  width: 220px;
  margin-left: 360px;
  padding: 5px;
  border-radius: 5px;
}

.filter i{
  color: white;
  margin-top: 3px;
  margin-right: 3px;
}

</style>