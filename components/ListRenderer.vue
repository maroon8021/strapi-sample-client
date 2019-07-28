<template>
  <div>
    <div v-for="item in data" :key="item.id" class="list-container">
      <nuxt-link :to="item.path" class="list-link">
        <h2 class="subtitle is-2">{{item.Title}}</h2>
        <div>
          {{item.Content}}
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: ['data']
}
</script>

<style lang="scss" scoped>
.list-container{
  padding: 16px 0;
}

.list-link{
  display: block;
  border: solid 2px #eeeeee;
  border-radius: 4px;
  padding: 8px;
}
</style>
