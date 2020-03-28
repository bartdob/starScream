<template>
  <div class="wrapper">
    <div class=search>
      <label for="search">Search</label>
      <input type="text"
      name="search"
      id="search "
      placeholder="YYYY-MM-DD"
      required pattern="(?:19|20)\[0-9\]{2}-(?:(?:0\[1-9\]|1\[0-2\])/(?:0\[1-9\]
      |1\[0-9\]|2\[0-9\])|(?:(?!02)(?:0\[1-9\]|1\[0-2\])/(?:30))|(?:(?:0\[13578\]|1\[02\])-31))"
      title="Enter a date in this format YYYY/MM/DD"
      v-model="searchValue"
      @input="handleInput"
      />
      <div style="max-height: 300px;">
        zdjecie
        <img :src="result" :key="1223"/>
      </div>

    </div>
  </div>
</template>

<script>
// const Api = 'https://api.nasa.gov/planetary/apod?api_key=JcJ60HqxjGiYm3YUc9471sFH2FxVgdpcTIJo5hIq';
const axios = require('axios');
const debounce = require('lodash.debounce');
// const fetchData = (date) => axios.get(`/fetch/${date}`);

export default
{
  name: 'Search',
  data() {
    return {
      searchValue: '',
      result: '',
    };
  },
  methods: {
    handleInput: debounce(function handle() {
      axios.get('https://api.nasa.gov/planetary/apod?api_key=JcJ60HqxjGiYm3YUc9471sFH2FxVgdpcTIJo5hIq&hd=true', {
        params: {
          date: this.searchValue,
        },

      })
        .then((response) => {
          console.log(response);
          this.result = response.data.hdurl;
          console.log('rezultat');
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
  padding: 30px;
  width: 100%;
  align-items: center;
  flex-direction: column;
}
.search{
  width: 300px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

input{
  border: 0;
border-bottom: 1px solid grey;
height: 30px;
}
</style>
