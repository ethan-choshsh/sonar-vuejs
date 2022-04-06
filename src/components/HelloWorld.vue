<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{ helloText }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      helloText: "",
    };
  },
  methods: {
    async hello() {
      let data = await axios
        .get("https://raw.githubusercontent.com/torvalds/linux/master/README")
        .then((res) => {
          return res.data;
        });
      this.helloText = data;

      data = 123;
    },
  },
  created() {
    this.hello();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
