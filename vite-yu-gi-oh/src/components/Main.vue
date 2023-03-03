<template>
    <main class="main">

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


        <ul class="characters">
  
          
          <Character v-for="element in store.characters" :key="element.id" :character="element" />
  
        </ul>
      </div>
    </main>
  </template>
  
  <script>
    import axios from 'axios'
    import store from '../store'
    import Character from './Character.vue'
    export default {
      components: {
        Character
      },
      data() {
        return {
          // characters: [],
          info: {},
          store,
          // store: store
        }
      },
      computed: {
        characters() {
          return this.store.characters
        }
      },
      methods: {
        fetchCharacters() {
          console.log('fetching data')
          // fare la chiamata in get all'endpoint: 
          axios
            .get('https://db.ygoprodeck.com/api/character')
            .then((res) => {
              console.log(res)
              console.log(res.data)
              console.log(res.data.info)
              this.store.characters = res.data.results
              // this.info = res.data.info
              const { count, pages } = res.data.info
              this.store.count = count
              this.store.pages = pages
              console.log(this.store)
            })
        }
      },
      created() {
        console.log('store',this.store)
        this.fetchCharacters()
      },
    }
  </script>
  
  <style lang="scss" scoped>
  .main {
    padding: 50px 0;
    background-color: #D48F38;
   
    
  }
  .container-main{
    width: 1000px;
    margin-left: 500px;
  }
  .characters {
    display: grid;
    gap: 40px;
    grid-template-columns: repeat(4,1fr);
    background-color: white;
    
  }

  /**MENU RULES */

  .menu {
    background-color: white;
    margin-bottom: 10px;
    display: flex;
    width: 120px;
    margin-left: 550px;
    padding: 5px;
    border-radius: 10px;
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