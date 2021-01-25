<template>
  <div class="app">
    <input type="text" v-model="number">
    <button @click="serchAddress">住所自動入力</button>
    <p>Address:{{getAddress}}</p>
  </div>
</template>

<script> 
import axios from "axios";
export default {
  data() {
    return {
      number: "",
      getAddress: ""
    }
  },
  methods: {
     serchAddress() {
      const url = "https://apis.postcode-jp.com/api/v4/postcodes/" + this.number
      console.log(url)
      axios.get(url).then(function(response) {
        this.getAddress = response.allAddress;
      })
    }
  }
}
</script>
