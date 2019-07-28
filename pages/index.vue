<template>
  <div class="container">
    <div>
      <h1 class="title is-1">
      <nuxt-link to="/">
        Strapi Sample
      </nuxt-link>
    </h1>
      <div class="links">
        <ListRenderer :data="lists"/>
      </div>
    </div>
  </div>
</template>

<script>
import ListRenderer from '~/components/ListRenderer.vue'
import axios from 'axios'

export default {
  components : {
    ListRenderer
  },
  data : () => ({
    lists : []
  }),
  asyncData ({params}) {
    return axios.get('http://localhost:1337/articles')
    .then((res) => {
      console.log('got data correctly')
      const lists = res.data.map((item) => {
        item.path = '/articles/' + item.id
        return item
      })
      console.log(lists)
      return {
        lists
      }
    })
    .catch((err) => {
      console.error(err)
    })
  }
}
</script>

<style>


</style>
