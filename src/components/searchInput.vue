<template>
<div class="searchInputWrapper">
    <div class="search">
      <label for="search">Search</label>
      <input type="date" class="text-center"
      data-date-format="YYYY-MM-DD"
      name="search"
      :class="{ dark }"
      id="search"
      placeholder="YYYY-MM-DD"
      required pattern="(?:19|20)\[0-9\]{2}-(?:(?:0\[1-9\]|1\[0-2\])/(?:0\[1-9\]
      |1\[0-9\]|2\[0-9\])|(?:(?!02)(?:0\[1-9\]|1\[0-2\])/(?:30))|(?:(?:0\[13578\]|1\[02\])-31))"
      title="Enter a date in this format YYYY/MM/DD"
      :value="value"
      @input="handleChange"

      />

    </div>
</div>

</template>

<script>
export default {
  name: 'searchInput',
  props: {
    value: {
      value: String,
      required: true,
    },
  },
  dark: {
    type: Boolean,
    default: false,
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.searchInputWrapper{
  display: flex;
  margin: 0;
  padding: 30px;
  width: 100%;
  align-items: center;
  flex-direction: column;
  // background-image: url("../assets/97.jpeg");
  color:white;
}
.search{
  width: 300px;
  display: flex;
  flex-direction: column;
  text-align: center;
  margin-top: 100px;
}

input{
border: 0;
border-bottom: 1px solid white;
height: 30px;
margin-top: 20px;
background: none;
color: grey;
transition: box-shadow 0.3s ease-in-out;
}
input:focus{
  outline: none;
  border-bottom: 1px solid yellow;
}
.dark{
  color: black;
  border-bottom-color: black;
}
p{
  margin-top: 200px;
}
.img{
  background: none;
}
</style>
