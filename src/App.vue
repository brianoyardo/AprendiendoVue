<template>
  <div class="nav-bar"></div>
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
        </ul>
      </div>
    </div>
  </article>
</template>

<script setup>
  const img = './src/assets/images/1.png'
  const prod = "Automoviles"
  //v-if
  const disponible = true
  const stock = 5

  const detalles = ["AT", "1198cc", "Automatica","Con Aros de Aluminio",8]
</script>

<style scoped>

</style>