<template>
  <div class="container">
    <h1 class="title is-1">
      <nuxt-link to="/">
        Strapi Sample
      </nuxt-link>
    </h1>

    <h2 class="title is-2">{{Title}}</h2>
    <h1>{{date}}</h1>

    <div>
      <img :src="imagePath" alt="main-image">
    </div>

    <div>
      {{Content}}
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data : () => ({
    Title : '',
    Content : '',
    imagePath : '',
    date : ''
  }),
  asyncData ({params}) {
    return axios.get('http://localhost:1337/articles/' + parseInt(params.id, 10))
    .then((res) => {
      console.log('got data correctly')
      const {Title, Content} = res.data
      console.log(res.data.url)
      return {
        Title,
        Content,
        imagePath : 'http://localhost:1337' + res.data.MainImage.url,
        date : res.data.created_at
      }
    })
    .catch((err) => {
      console.error(err)
    })
  }
}
</script>
