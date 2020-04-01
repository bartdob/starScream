<template>
<div class="starImage" />
</template>

<script>
export default {
  name: 'starImage',
};
</script>

<style lang="scss" scoped>
.starImage{
  padding: 0;
  margin: 0;
  position: fixed;
  background-image: url("../assets/97.jpeg");
  height: 100vh;
  width: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-color: black;
  font-family: 'Comic Neue', cursive;
  z-index: -1;
}

.starImage::after{
    content: '';
    position: absolute;
    top: 0;
    z-index: 1;
    width: 100%;

}
</style>
