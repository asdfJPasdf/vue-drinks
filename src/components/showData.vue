<template>
  <div class="card" style="width: 18rem;">
  <img class="card-img-top" src= {{image}} alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">{{name}}</h5>
    <p class="card-text">{{description}}</p>
  </div>
  <ul class="list-group list-group-flush">
    <li class="list-group-item">{{ingredients}}</li>
    <li class="list-group-item"></li>
    <li class="list-group-item"></li>
  </ul>
  <div class="card-body">
    <a href="#" class="card-link">Card link</a>
    <a href="#" class="card-link">Another link</a>
  </div>
</div>
</template>

<script>
export default {
    props:{
        name:{
            type: String,
            require: true,
        },
        description:{
            type:String,
            require: false,
        },
        image:{
            type:String,
            require:false,

        
        },
        ingredients:{
            type: String,
            require:false,

        }


    }

}
</script>

<style>

</style>