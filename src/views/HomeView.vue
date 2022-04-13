<template>

<div style="position:absolute; top:0px; right:0px;" >
       <input type="text" placeholder="Suche..." class="form-control-sm" v-model="inputName" >
        <br> 
    </div> 

  <showData
  :description="description"
  :image="image"
  :name="name"
  :ingredients="ingredients"
  />
</template>

<script>
// @ is an alias to /src
import showData from '@/components/showData.vue';
import axios from "axios";

export default {
  name: 'HomeView',
  components: {
    showData
  },
  data() {
    return {
      description: "",
      image: "",
      name:"",
      ingredients: "",
      inputName:"",  
      data:[],
    }
  },
  async created(inputName) {
    try {
      const resCategories = await axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${inputName}`);
      this.categories = resCategories.data;
    } catch (error) {
      console.log(error);
    }
  },
methods:
{

}
}
</script>
