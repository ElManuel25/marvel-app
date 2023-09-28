<template>
  <div class="layout-container">

    <div class="page-content">

      <div class="navbar">

        <div class="logo">
          <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Marvel_Logo.svg/2560px-Marvel_Logo.svg.png"
            alt="Logo Marvel">
        </div>

        <div class="title-container">
          <div class="title">
            Marvel Heroes
          </div>
        </div>

        <div class="gif-container">
          <img src="https://media.tenor.com/Q4qyZizrNGMAAAAj/thor-love-and-thunder-marvel-studios.gif" alt="GIF"
            class="gif-image">
        </div>
      </div>


      <main>

        <slot />
      </main>
    </div>
  </div>
</template>

<style scoped>
.layout-container {
  background-color: rgb(187, 13, 13);
}

.page-content {
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

.gif-image {
  max-width: 50px;
}
</style>