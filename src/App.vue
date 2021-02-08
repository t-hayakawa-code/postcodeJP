<template>
  <div id="app">
    <div class="location">
      <input type="text" maxlength="7" v-model="address">
      <button @click="transition()">住所自動入力</button>
      <p>Address: {{ postData }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      address:"",
      postData:""
    };
  },
  methods: {
      async transition() {
            const item = await axios.get(
            `https://apis.postcode-jp.com/api/v4/postcodes/${this.address}?&apikey=0UhyXr2fh2vCgeCvl4pYcsLx4aeZbPJwFZSYjcu`);


            this.postData = item.data[0].allAddress;
          }
      }
  };
</script>



<style>
#app {
  display: flex;
}

</style>