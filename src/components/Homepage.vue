<template>
        <v-form class="container">
            <div>
            <v-text-field type="text" v-model="searchString" placeholder="Enter anything to look for recipe"></v-text-field>
            </div>
            <div v-for="recipe in result" :key="recipe">
                <h2>{{ recipe }}</h2>
            </div>
        </v-form>
</template>

<script>
import axios from 'axios'
import API_KEY from '../config.js'

export default {
  name: 'Homepage',
  data: function(){
      return {
          searchString: '',
          err: '',
          recipes: []
      }
  },
  created: function(){
      var self = this;
      axios.get('https://www.food2fork.com/api/search?key='+ '67cbf1c3e7e4b645cc51034511cdb7b8' +'&q='+ this.searchString)
      .then((result) => { 
          this.result = result.data
          })
      .catch((err) => { this.err = err })
  }
}
</script>
