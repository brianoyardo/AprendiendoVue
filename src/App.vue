<template>
  <div class="nav-bar"><div class="cart">Carrito({{cart.length}})</div></div>
  <article class="product-display">
    <Producto :tipo-cliente="tipoCliente" @inc="inc"/>
  </article>
</template>

<script setup>
import { computed, ref } from 'vue';
import Producto  from "./components/Producto.vue"
  //carrito
  const cart = ref([]);
  const inc = (id) => cart.value.push(id);//Nose que tenia que anotar pero tenia que tener cuidado con estaparte porque hay algunas cosas que no puedes funcionar en la reactividad
  /* const updateImg = (image) =>{
    img.value = image
  } */


  //PROPS
  const tipoCliente = "vip"
</script>

<style scoped>

</style>