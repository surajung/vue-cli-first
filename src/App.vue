<template>
  <div id="app">
    <button @click="fetchPosts">불러오기</button>
    <ul>
      <li v-for="post in posts">
        <h1>{{ post.title }}</h1>
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      posts: []
    }
  },
  methods: {
    fetchPosts () {
      this.axios.get('https://jsonplaceholder.typicode.com/posts')
      .then((response) => {
        console.log(response)
        this.posts = response.data
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-align:left;
}
</style>
