<template>
  <div>
    Welcome <span style="color: lightpink">{{githubUserName}}</span>!
    <img :src="avatar_url" alt="My Github Avatar">
    <a :href="html_url">My Github Home page</a>
  </div>
</template>
<script>

export default {
  data () {
    return {
      code: '',
      accessToken: '',
      githubUserName: 'dummyUserName',
      avatar_url: '',
      html_url: ''
    }
  },
  mounted () {
    this.code = this.$route.query.code
    this.$http.post(`/api/oauth/${this.code}`).then((res) => {
      let result = res.data.data
      this.githubUserName = result.login
      this.avatar_url = result.avatar_url
      this.html_url = result.html_url
    })
  }
}
</script>
