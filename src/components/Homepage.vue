<template>
        <v-form class="container">
            <div class="searchbox">
                <v-text-field type="text" v-model="searchString" placeholder="Enter anything to look for recipe"></v-text-field>
                 <v-btn v-on:click="submit" flat>search</v-btn>
            </div>
                <v-container fluid>
                 <v-layout>
                     <v-flex>
                        <div v-for="recipe in recipes" :key="recipe.id" class="box">
                            <a :href="recipe.source_url">
                            <small><img :src="recipe.image_url"></small>
                            <strong>{{ recipe.title }}</strong><br /></a>
                        </div>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-form>
</template>

<script>
import axios from 'axios'
import Content from '@/components/Content'

export default {
  name: 'Homepage',
  components: {
    Content
  },
  data: () => {
      return {
          searchString: '',
          err: '',
          recipes: [],
      }
  },
  methods: {
      submit () {
          var self = this;
          axios.get('https://www.food2fork.com/api/search?key='+ '67cbf1c3e7e4b645cc51034511cdb7b8' +'&q='+ this.searchString)
          .then((result) => {
              this.recipes = result.data.recipes.slice(0, 10);
              console.log(recipes)
          })
          .catch((err) => { this.err = err })
      },

  }
}
</script>

<style scoped>
    .searchbox{
    display: flex;
    justify-content: center;
    align-items: center;
    }

    .box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: 0 1px 3px 0 rgba(0,0,0,.15);;
    min-height: 150px;
    border-radius: 5px;
    background-color: white;
    padding-left: 10px;
    padding-right: 10px;
    float: left;
    width: 50%;
    }

    img {
        width: 20%;
        height: 20%;
    }

    a {
    text-decoration: none;
}
</style>
