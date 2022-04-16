<template>

<div  >
       <input type="text" placeholder="Suche..." class="form-control-sm" v-model="inputName"  @keyup.enter="created">
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
      id:0,
      description: "",
      image: "",
      name:"",
      ingredients: [],
     inputName:"",  
      infos:[],
    }
  },
  async created() {
    try {
      
      const resInfos = await axios.get(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${this.inputName}`);
      this.infos = resInfos.data;
    } catch (error) {
      console.log(error);
    }
    console.log(this.infos['drinks'][0]['strDrinkThumb']);
    this.name=this.infos['drinks'][0]['strDrink'];
    this.description=this.infos['drinks'][0]['strInstructionsDE'];
    this.image=this.infos['drinks'][0]['strDrinkThumb'];
    do{
      let x= 1;
      var notEmpty=true;
     if(this.infos['drinks'][0][`strIngredient${x}`]!=null){
       this.ingredients.push(this.infos['drinks'][0][`strIngredient${x}`]);
      x++;
     }
     else {notEmpty=false;}
    
    
    }while (notEmpty)

  },
  
methodes:{


}
}
</script>
