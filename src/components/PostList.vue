<template>
  <div v-show="posts.length > 0">
    <h3>User List</h3>
    <post-item class="post" 
      :post="post"
      v-for="post in posts" 
      :key="post.id"
      @remove="this.$emit('remove', post)"/>
  </div>
  <h2 v-show="posts.length === 0" style="color: red;">
    No Post was added yet
  </h2>
</template>

<script>
import PostItem from '@/components/PostItem'
  export default {
    components: {PostItem},
    props: {
      posts: {
        type: Array,
        required: true
      }
    }
    
  }
</script>

<style scoped>

</style>