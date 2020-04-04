<template>
  <div class="wrapper">
    <transition name="fade">
      <starImage v-if="step === 0"/>
    </transition>
    <Claim v-if="step === 0" />
    <searchInput v-model="searchValue" @input="handleInput" :dark="step === 1" />
        <div class="container">
          <div class="img">
            <p v-html="desc"/>
              <a :href="result">
                <img :src="result" class="img-thumbnail" :key="1223"/>
              </a>
          </div>
        </div>
  </div>
</template>

<script>
import Claim from '../components/Claim.vue';
import searchInput from '../components/searchInput.vue';
import starImage from '../components/starImage.vue';


const axios = require('axios');
const debounce = require('lodash.debounce');


export default
{
  name: 'Search',
  components: { starImage, Claim, searchInput },
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      result: '',
      desc: '',
    };
  },
  methods: {
    handleInput: debounce(function handle() {
      this.loading = true;
      console.log(this.searchValue);
      axios.get('https://api.nasa.gov/planetary/apod?', {
        params: {
          date: this.searchValue,
          api_key: '*******************************',
          hd: true,
        },

      })
        .then((response) => {
          console.log(response);
          this.result = response.data.hdurl;
          this.desc = response.data.explanation;
          console.log(this.desc);
          this.loading = false;
          this.step = 1;
          // this.result = this.searchValue;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 700),
  },
};

</script>

<style lang="scss" scoped>
.wrapper{
  display: flex;
  margin: 0;
  padding: 0px;
  width: 100%;
  align-items: center;
  flex-direction: column;
}
a, img{
  background: none;
  border: none;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
