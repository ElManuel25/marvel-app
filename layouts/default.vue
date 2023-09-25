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
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Marvel_Logo.svg/2560px-Marvel_Logo.svg.png" alt="Logo Marvel">          </div>
          <!-- Texto en el centro -->
          <div class="title-container">
            <div class="title">
              Marvel Heroes
            </div>
          </div>
        </div>
  
        <!-- 80% contenido -->
        <main>
          <!-- Utilizando el slot para cargar el contenido de la página -->
          <div class="slot-container">
            <slot></slot>
          </div>
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
  
  .left-margin, .right-margin {
    flex: 1;
    background-color: #f0f0f0;
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
  
  .main {
    text-align: center;
  }
  
  .slot-container {
    flex-grow: 1;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  </style>
  