<template>
  <div v-for="(x, i) in posts" :key="i" >
    <h5 @click="$router.push(`/detail/${i}`)">{{ posts[i].title }}</h5>
    <p>{{ posts[i].date }}</p>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    posts: Array
  }
}
</script>

<style>

</style>