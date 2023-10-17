<template>
    <div class="product-container">
      <div class="product-image">
        <img :src="img" alt="Lambourus">
      </div>
      <div class="product-info">
        <!-- <h1>{{ prod +" "+ marca}}</h1>  Para no hacer esto-->
        <h1>{{ tittle}}</h1> <!-- Antes era prod, pero se concatena con las operaciones compuadas -->
        <!--  if -->
        <!-- <p v-if="disponible">Disponible</p>
        <p v-else>Agotado</p> -->
        <!-- v-show -->
        <!-- <p v-show="disponible">Disponible</p> -->

        <p v-if="stock>10">Variedad de Colores y Equipamiento</p>
        <p v-else-if="stock<=10 && stock>0">Pocas Unidades. Adquiera el suyo</p>
        <p v-else>Agotado</p>

        <p>Descuento: {{ desc }}</p>

        <ul>
          <!-- Uso del v-for -->
          <li v-for="d in detalles">
            {{ d }}
          </li>
          <div v-for="(v, i) in variantes" :key="v.id" @mouseover="updateImg(i)" class="color-circle" :style="{backgroundColor: v.color}"></div>
          <!-- <button class="btn" v-on:click="cart++" >Añadir al carrito</button> -->
          <button class="btn" @click="$emit('inc', variantes[selectedVariant].id)" :class="{disablebtn: !stock}" :disabled="!stock">Añadir al carrito</button>
          <button v-if="cart!=0" class="btn" @click="$emit('inc')">Quitar del carrito</button>
        </ul>
      </div>
    </div>
</template>

<script setup>
const props = defineProps(['tipoCliente'])
import { computed, ref } from 'vue';

  //const img = ref('./src/assets/images/1.png')
  const prod = "Automoviles"
  //v-if
  const disponible = true
  //const stock = 5

  const detalles = ["AT", "1198cc", "Automatica","Con Aros de Aluminio",8]
  const variantes = [
    {id: 1, color: "blue" , img: "./src/assets/images/1.png",stock: 15},
    {id: 2, color: "yellow" , img: "./src/assets/images/2.png",stock: 5},
    {id: 3, color: "green", img: "./src/assets/images/3.png",stock: 0}
  ];

  const updateImg = (i) =>{ //i es el indice
    selectedVariant.value = i
  }

  //Propiedades Computadas
  const marca = "Lamborguini"

  const selectedVariant = ref(0);

  const tittle = computed(()=>prod +" "+marca)//se le puede poner llaves
  const img = computed(()=>variantes[selectedVariant.value].img)
  const stock = computed(()=>variantes[selectedVariant.value].stock)

  const desc = computed(()=>{
    return props.tipoCliente=="regular"?"5%":"30%"
  })  
</script>

<style scoped>

</style>