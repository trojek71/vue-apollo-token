<template>
  <div class="hello">
    <div v-for="post in posts" :key="post.id">
    {{post.title}}</div>
  </div>
</template>

<script>
import gql from "graphql-tag"
export default {
  name: 'about',
  props: {
    msg: String
  },
  apollo: {
    posts: gql `
      query {
        posts{
          id
          title
          content
          createdAt
          updatedAt
        }
      }`,
    
  }
}

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
