<template>
  <div class="hello">
    <a :href="generateLoginToGithubLink()">click me to login with github</a>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      clientId: '07f767ab8f2bc709ad24',
      clientSecret: '4af29c4f5b5966acfd7d0dc0d4bceb9bc3fe38ef',
      redirectUri: 'http://localhost:9444/oauth/redirect'
    }
  },
  methods: {
    generateLoginToGithubLink () {
      return `https://github.com/login/oauth/authorize?client_id=${this.clientId}&redirect_uri=${this.redirectUri}&login=FelicityAmiao`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
