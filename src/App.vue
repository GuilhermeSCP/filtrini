<template>
  <div id="vueapp">
    <img src="https://s3.eu-west-1.amazonaws.com/pocflagship/vueapp/logo.png">
    <ul>
      <li v-for="term in searchTerms">
        {{ term }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'vueapp',
  data () {
    return {
      searchTerms: [],
    }
  },
  methods: {
    addKeyword: function (keyword) {
      this.searchTerms = [...this.searchTerms, keyword];
    }
  },
  mounted () {
    document.addEventListener('team-search', (e) => {
      this.addKeyword(e.detail);
    });
  }
}
</script>

<style>
#vueapp {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  float: left;
  padding: 1em 2em;
}

#vueapp img {
  height: 25px;
  display: inline-block;
  vertical-align: middle;
}

#vueapp ul {
  display: inline-block;
  vertical-align: middle;
  list-style-type: none;
  padding: 0;
}

#vueapp li {
  display: inline-block;
  margin: 0 10px;
}

#vueapp a {
  color: #42b983;
}
</style>
