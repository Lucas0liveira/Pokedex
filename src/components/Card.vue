<template>
  <div class="card">
    <div class="pokemon">
      <p>#1</p>
      <img class="imgPoke" alt="Bulbassauro" src="../assets/bulba.png"  style="height: 120px;"/> 
      </div>

      <p class="nomePoke"> Nome do pokemon</p>
    
    <div class="tipos">
      <p class="tipo"> Tipo 01 </p> 
      <p class="tipo"> Tipo 02 </p>
  
    </div>
    </div>  
</template>

<script>
</script>

<style>

body{
}
.card{
  display:flex;
  flex-direction: column;
  width:196px;
  height:280px;
  border:solid 2px #666666;
  border-radius: 5px;
  background-color: #FFFFFF;
}
.pokemon{
  background-color:greenyellow;
  height: 100;
  border-radius: 5px; 
  border-bottom: solid 1px #141414;
}
.imgPoke{
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.nomePoke{
  text-align: center;
  font-size: 20px;
}
.tipo{  
  background-color: #f1f1f1;
  margin: 2px;
  padding: 5px;
  font-size: 15px;
}
.tipos{
  display: flex;
  justify-content: center;
}
</style>