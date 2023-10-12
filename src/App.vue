<template>
  <div class="nav-bar"><div class="cart">Carrito({{cart}})</div></div>
  <article class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="img" alt="Lambourus">
      </div>
      <div class="product-info">
        <h1>{{ prod }}</h1>
        <!--  if -->
        <!-- <p v-if="disponible">Disponible</p>
        <p v-else>Agotado</p> -->
        <!-- v-show -->
        <!-- <p v-show="disponible">Disponible</p> -->

        <p v-if="stock>10">Variedad de Colores y Equipamiento</p>
        <p v-else-if="stock<=10 && stock>0">Pocas Unidades. Adquiera el suyo</p>
        <p v-else>Agotado</p>
        <ul>
          <!-- Uso del v-for -->
          <li v-for="d in detalles">
            {{ d }}
          </li>
          <div v-for="v in variantes" :key="v.id" @mouseover="updateImg(v.img)" class="color-circle" :style="{backgroundColor: v.color}"></div>
          <button class="btn" v-on:click="cart++">Añadir al carrito</button>
          <button v-if="cart!=0" class="btn" @click="inc()">Quitar del carrito</button>
        </ul>
      </div>
    </div>
  </article>
</template>

<script setup>
import { ref } from 'vue';

  const img = ref('./src/assets/images/1.png')
  const prod = "Automoviles"
  //v-if
  const disponible = true
  const stock = 5

  const detalles = ["AT", "1198cc", "Automatica","Con Aros de Aluminio",8]
  const variantes = [
    {id: 1, color: "blue" , img: "./src/assets/images/1.png"},
    {id: 2, color: "yellow" , img: "./src/assets/images/2.png"},
    {id: 3, color: "green", img: "./src/assets/images/3.png"}
  ];
  //carrito
  const cart = ref(0);
  const inc = () => cart.value--;//Nose que tenia que anotar pero tenia que tener cuidado con estaparte porque hay algunas cosas que no puedes funcionar en la reactividad
  const updateImg = (image) =>{
    img.value = image
  }
</script>

<style scoped>

</style>