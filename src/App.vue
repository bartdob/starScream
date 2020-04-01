<template>
  <div class="app">
    <div class="navbar navbar-dark bg-dark">
              <router-link class="routerlink" to="/">STAR SCREAM</router-link>
              <router-link class="routerlink" to="/about">about</router-link>
    </div>
      <router-view/>
  </div>
</template>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css?family=Comic+Neue:300i,400,700&display=swap');

*
{
  box-sizing: border-box;
}

.routerlink{
  color: white;
}


.app{
  // background-image: url("assets/97.jpeg");
  height: 100vh;
  width: 100%;
  background-size: 'cover';
  background-repeat: no-repeat;
  background-position: center;
  // background-color: black;
  font-family: 'Comic Neue', cursive;
}
</style>
