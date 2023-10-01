<script setup>
// colocacion de la reactividad
import {ref, computed, createCommentVNode} from 'vue'

//variable constante  
const contar = 0;

/*variable que puede ser
modificada con la reactividad, para acceder necesita " variable.value " ya que devuelve un objeto
 */
const reactivo = ref(0);

const restar = ref(0);

//metodo 
const incremento = () => {
  reactivo.value++;
}

const decrementar = () => {
  reactivo.value--;
}

const resetear = () => {
  reactivo.value = 0;
}


const bloqueobtn = computed (() => {
const busqueda = array.value.find(num => num === reactivo.value) 
console.log(busqueda);

if(busqueda === 0) return true;
return busqueda ? true : false;

})

const classContador = computed (() =>{
  if(reactivo.value === 0){
    return 'cero'
  }

  if(reactivo.value > 0 ){
return 'positivo'
  }

  if(reactivo.value < 0){
    return 'negativo'
  }
});



// funcion de flecha 
const add = () => {
array.value.push(reactivo.value)
}

//carga de nuevos numeros a ingresar
const array = ref([]);


</script>


<template>

  <div class="container text-center mt-1">
    <h1>desarrollando con Vue js</h1><br>   
  <h2 :class="classContador"> {{ reactivo }}</h2>

  <button @click="incremento" class="btn btn-success"> Incrementar </button><br>
  <button @click="decrementar" class="btn btn-danger">Disminuir</button><br>   
  <button @click="resetear" class="btn btn-secondary">Resetar</button><br>
  <button @click="add" :disabled="bloqueobtn" class="btn btn-primary">Agregar</button><br>
{{ array }}

<ul class="list-group">
  <li class="list-group-item mt-2" v-for="(num, index) in array" :key="index">

    {{ num }}

  </li>
</ul>

  </div>
  
</template>  

//kakc
<style>   

h1{
  color: aqua;        
  text-align: start;
  margin: 0%;

}

.positivo{
  color: rgb(73, 60, 161);
} 

.negativo{
  color: red;
}

.cero {
  color:rgb(90, 0, 122);
}
</style>