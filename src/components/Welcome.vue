<template>
  <div>
    Welcome <span style="color: lightpink">{{githubUserName}}</span>!
    <img :src="avatar_url" alt="My Github Avatar">
    <a :href="html_url">My Html Url</a>
  </div>
</template>
<script>

import * as axios from 'axios'

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
      this.accessToken = res.bodyText
      axios({
        method: 'get',
        url: `https://api.github.com/user`,
        headers: {
          accept: 'application/json',
          Authorization: `token ${this.accessToken}`
        }
      }).then(res => {
        this.githubUserName = res.data.login
        this.avatar_url = res.data.avatar_url
        this.html_url = res.data.html_url
      })
    })
  }
}
</script>
