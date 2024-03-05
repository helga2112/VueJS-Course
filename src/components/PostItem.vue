<template>
  <div class="post">
    <div><strong>Title:</strong> {{ post.title }}</div> 
    <div><strong>Description:</strong> {{ post.body }}</div> 
    <div class="post__buttons">
      <my-button
        @click="this.$emit('remove', post)">Delete</my-button>
      <my-button>Edit</my-button>
    </div>
</div>
</template>

<script>
import MyButton from '@/components/UI/MyButton'
  export default {
    components:{
      MyButton
    },
    props: {
      post: {
        type: Object,
        required: true
      }
    }
    
  }
</script>

<style scoped>
.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

</style>