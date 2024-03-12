<script setup>
// Importando funcion
// para crear referencias reactivas
import { ref } from 'vue'
// Creando una referencia reactiva
// de tipo string
const header = ref('App lista de compras');
const shoppingIcon = ref('material-icons shopping-cart-icon');
// Creando una referencia reactiva
// para alamacenar el valor de la lista
const items = ref([
  { id: 0, label: 'Leche' },
  { id: 1, label: 'Arroz' },
  { id: 2, label: 'Carne' },
  { id: 3, label: 'Pan' },
  { id: 4, label: 'Huevos' }
]);
const newItem= ref(''); 
//metodos
const saveItems = () =>{(items.value.push({id: items.value.length, label:newItem.value}));
newItem.value="";}
</script>

<template>
  <h1> <i :class="shoppingIcon">local_mall</i> {{ header }}</h1>
  <form 
  v-on:submit.prevent="saveItems"
  class="add-item" form>
    <input 
     v-model="newItem" type="text"
      placeholder="Agregar articulo">
   <label>
    <input  type="checkbox" v-model="newItemHighPriority">
    Alta pioridad
  </label >
   <!-- boton-->
   <button class="btn btn-primary">
    Agregar articulo
  </button>
   {{ newItemHighPriority ? '🍻' : '🏆'}}
    
</form>
 <ul>
    
    <li v-for="({id, label} ) in items" v-bind:key="id" >🍻 {{ label }}🍻</li>
    

<!--Helados (label>input:checkbox{Flavor$})*3-->

</ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>