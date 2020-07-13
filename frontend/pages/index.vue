<template>
  <div v-cloak class="container">
    <ul>
      <li v-for="(article, key) in articles" :key="key">
        <nuxt-link :to="'/blog/'+article.id">
          {{ article.Title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get('http://localhost:1337/blogs')
    return { articles: data }
  }
}
</script>

<style>
[v-cloak] {
  display: none;
}
</style>
