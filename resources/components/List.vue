<template>
    <div class="list_card pl-5 pt-5">
        <Searchbar  :beers="beers"/>
        <div class="list_bar">
        <ul>
        <li v-for="beer in beers" :key="beer.id" >
            <nuxt-link :to="'/'+beer.id" class="no-underline text-black">
            {{beer.name}}
            </nuxt-link>
        </li>
        </ul>
        </div>    
    </div>
</template>
<script>
import axios from "axios";
import Searchbar from '@/components/Searchbar'
export default {
  data() {
    return {
      beers : []
  }}, 
  components: {
        Searchbar  
  },
  created () {
        axios.get(`https://api.punkapi.com/v2/beers`)
                    .then(response => {
                        this.beers = response.data
                        console.log(this.results[0].link)
                    });
       
  },
};
</script>
<style scoped> 
*{
  color: #F4F6E7;
  font-family: 'Roboto Slab', serif;
  font-weight: 400;
}
.search_bar {
    position: fixed;
    z-index: 9999;
}

.list_bar {
    position: relative;
    margin-top: 70px;
}
#search {
  width: 250px;
  height: 40px;
  border: 3px solid #89806E;
  transition: 0.1s;
  padding: 3%;
  margin-bottom: 5%;
  color:  #382611;
}
#search:focus {
    transform: scale(1.1);
    border: 5px solid #89806E;
}
#search:hover {
    border: 5px solid #89806E;
}
ul {
  position: relative;
  margin-top: 30px;
}
li {
  list-style-type: none;
  text-decoration: none;
  line-height: 2.5;
  margin-left: -10%;
  margin-top: 3% ;
  transition: 1s;
  text-transform: uppercase;
  font-size: 70%;
  z-index: 9999;
}
li:hover {
  
  transform: scale(1.0);
  padding-left: 10%;
  font-size: 100%;
  z-index: 9999;
}
li:active {
  color: #a5a0a0;
}
.list_card {
  background-color: #382611;
  padding-right: 5%;
  overflow-y: auto;
  height: 100vh;
}
::-webkit-scrollbar {
    width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
    box-shadow: inset 0 0 5px  #F4F6E7; 
    border-radius: 0px;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
    background:  #F4F6E7; 
    border-radius: 0px;
    height: 0px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
    background: grey; 
}
</style>


