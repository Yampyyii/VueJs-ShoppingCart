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
const newItemHighPriority = ref('') 
</script>

<template>
  <h1> <i :class="shoppingIcon">local_mall</i> {{ header }}</h1>
  <div class="add-item form">
    <input
     v-on:keyup.enter="items.push({id: items.length, label:newItem})" v-model="newItem" type="text" placeholder="Agregar articulo">
   <label>
    <input  type="checkbox" v-model="newItemHighPriority">
    Alta pioridad
  </label >
   <!-- boton-->
   <button class="btn btn-primary" v-on:click="items.push({id: items.length, label:newItem})">
    Agregar articulo
  </button>
   {{ newItemHighPriority ? '🍻' : '🏆'}}
    
  </div>
 <ul>
    <if>
    <li v-for="({id, label}, i) in items" v-bind:key="id" >🍻 {{ label }}🍻</li>
    
  </if>
<!--Helados (label>input:checkbox{Flavor$})*3-->

</ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>