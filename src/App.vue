<template class="stars">
  <div class="app">
    <div class="navbar navbar-dark bg-dark">
              <router-link class="routerlink" to="/">STAR SCREAM</router-link>

              <router-link class="routerlink" to="/about">about</router-link>
    </div>
      <router-view/>
  </div>
</template>

<style lang="scss" scoped>
.routerlink{
  color: white;
}
.app{
  background-image: url("assets/97.jpeg");
  height: 1000px;
  background-size: 'cover';
}
</style>
