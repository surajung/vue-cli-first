<template>
  <div id="app">
    <button @click="fetchPosts">불러오기</button>
    <ul class="type01">
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
    fetchPosts () { // es5 : function fetchPosts ()
      this.axios.get('https://jsonplaceholder.typicode.com/posts', {
        params: {
          userId: 1
        }
      }).then((response) => { // es5 : .then(function(response) {}).bind(this)
        console.log(response.data)
        this.posts = response.data
      })
    }
  }
}
</script>

<style lang="scss">
$point-color: #123456;
ul.type01 {
  li {
    h1 {font-size: 20px;color:$point-color;}
    p {font-size: 12px;color:blue;}
  }
}
</style>
