<template>
  <main class="main">

    <!-- INPUT PER RICERCARE LA CARTA IN BASE AL NOME -->
    <Filters @filter="fetchCards" />

    
    <!-- Menù dropdown -->
    <div class="menu">
      <ul>
        <li class="dropdown">
          <a href="#" class="alien">Alien</a> <i class="fa-solid fa-chevron-down"></i>
          <div class="dropdown-content">
            <a href="#">Fedele della luce</a>
            <a href="#">Ala Nera</a>
            <a href="#">Gladiatore Bestia</a>
          </div>
        </li>
      </ul>
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
export default {
  components: {
    Card
  },
  data() {
    return {
      cards: []
    }
  },
  methods: {
    fetchCards() {
      console.log('fetching data')
      axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
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
.menu {
  background-color: white;
  margin-bottom: 25px;
  display: flex;
  width: 120px;
  margin-left: 360px;
  padding: 5px;
  border-radius: 5px;
}
.dropdown-content {
  display: none;
  position: absolute;
  z-index: 1;
}
.dropdown:hover .dropdown-content {
  display: block;
}
.dropdown-content a {
  display: block;
  padding: 10px;
  background-color: #f9f9f9;
  color: #333;
  text-decoration: none;
  text-align: left;
}
.dropdown-content a:hover{
  color: red;
}
.alien {
  padding-right: 40px;
}
</style>