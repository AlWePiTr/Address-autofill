<template>
  <div class="app">
    <input type="text" v-model="number">
    <button @click="serchAddress">住所自動入力</button>
    <p>Address:{{ getAddress }}</p>
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
      axios.get(url).then((response)=> {
        console.log(this);
        this.getAddress = response.data[0].allAddress;
      })
      var self = this
      axios.get(url).then(function(response) {
        console.log(this);
        self.getAddress = response.data[0].allAddress;
      })
    }
  }
}
</script>
