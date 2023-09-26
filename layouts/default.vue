<template>
  <div class="layout-container">
    <!-- 10% margen izquierdo -->
    <div class="left-margin"></div>

    <!-- Contenido de la página -->
    <div class="page-content">
      <!-- Barra de navegación -->
      <div class="navbar">
        <!-- Logo a la izquierda -->
        <div class="logo">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Marvel_Logo.svg/2560px-Marvel_Logo.svg.png"
            alt="Logo Marvel">
        </div>
        <!-- Texto en el centro -->
        <div class="title-container">
          <div class="title">
            Marvel Heroes
          </div>
        </div>
        <!-- Nueva div para el GIF -->
        <div class="gif-container">
          <img src="https://media.tenor.com/Q4qyZizrNGMAAAAj/thor-love-and-thunder-marvel-studios.gif" alt="GIF" class="gif-image">
        </div>
      </div>

      <!-- 80% contenido -->
      <main>
        <!-- Utilizando el slot para cargar el contenido de la página -->
        <slot />
      </main>
    </div>

    <!-- 10% margen derecho -->
    <div class="right-margin"></div>
  </div>
</template>

<style scoped>
.layout-container {
  display: flex;
  height: 100%;
}

.left-margin,
.right-margin {
  flex: 1;
  background-image: repeating-linear-gradient(rgb(253, 0, 0), #f2ff00 15%, #ff0000 30%);
  min-height: 100%;
  /* Asegura que el contenedor tenga un tamaño mínimo */
}

.page-content {
  flex: 8;
  display: flex;
  flex-direction: column;
}

.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  background-color: #f0f0f0;
}

.logo img {
  height: 30px;
}

.title-container {
  flex-grow: 1;
  text-align: center;
}

.title {
  font-size: 24px;
  font-weight: bold;
}

main {
  flex-grow: 1;
  /* Ocupa todo el espacio disponible */
}

.slot-container {
  flex-grow: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}
  
.gif-image {
  max-width: 50px; /* Cambia el tamaño máximo del GIF según lo necesites */
}

</style>
