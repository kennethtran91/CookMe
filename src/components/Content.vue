<template>
    <v-container fluid>
                 <v-layout>
                     <v-flex>
                        <div v-for="recipe in recipes" :key="recipe.id" class="box">
                            <small><img :src="recipe.image_url"></small>
                            <strong>{{ recipe.title }}</strong><br />
                        </div>
                    </v-flex>
                </v-layout>
            </v-container>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Content',
    data: () => {
      return {
          err: '',
          recipes: [],
      }
  },
  mounted () {
            var self = this;
            // axios.get('https://www.food2fork.com/api/search?key='+ '67cbf1c3e7e4b645cc51034511cdb7b8' +'&q='+ this.searchString)

            axios.get('https://jsonplaceholder.typicode.com/posts')
            .then((result) => { 
            // this.recipes = result.data.recipes.slice(0, 10);
            this.recipes = result.data.slice(0, 10);
            console.log(recipes)
             })
        .catch((err) => { this.err = err })
  }
   
}
</script>

<style scoped>
    .box{
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

    img{
        width: 20%;
        height: 20%;
    }
</style>
