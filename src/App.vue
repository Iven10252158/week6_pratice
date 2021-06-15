<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-success">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav fw-bold">
        <li class="nav-item">
          <router-link to="/" class="nav-link">Home</router-link>
        </li>
        <li class="nav-item">
           <router-link to="/about" class="nav-link">About</router-link>
        </li>
        <li class="nav-item">
           <router-link to="/products" class="nav-link">產品列表</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>
<div class="container">
  <router-view/>
</div>
</template>

<style lang="scss">
  @import './assets/all';
</style>
