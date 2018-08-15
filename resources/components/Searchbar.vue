<template>
    <div>
        <div class="search_bar">
            <input id="search" type="text" placeholder="Search for name" v-model="textSearch" @keyup.enter="search" >
            <ul class="search_bar-dropdown">
                <li v-for="beer in listName" :key="beer.id">
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
export default {
  props: ["beers"],
  data() {
    return {
      textSearch: "",
      listName: [],
      json: []
    };
  },
  methods: {
      async search() {
      let json = await axios.get("https://api.punkapi.com/v2/beers?beer_name=" + this.textSearch)
      console.log(json)
      this.listName = json.data;
      if (this.listName.length == 0) {
          this.listName = [{name: "Can't find the results"}];
      } else if (this.textSearch == null) {
          this.listName = []
      }
  },
    
  },
  watch: {
    textSearch: function() {
      setTimeout(this.search, 500);
    }
  }
};
</script>

<style scoped>
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
  border: 5px solid #89806e;
  transition: 0.1s;
  padding: 3%;
  margin-bottom: 5%;
  color: #382611;
}
#search:focus {
  border: 5px solid #89806e;
}
#search:hover {
  border: 5px solid #89806e;
}
ul {
  margin-top: -5%;
  list-style-type: none;
  background-color: white;
  z-index: 9999;
  color: #382611;
  width: 250px;
}
li {
  border-bottom: 1px solid #382611;
  margin-left: -17%;
  font-size: 20px;
}
li:hover {
  color: #ffa320;
}
</style>