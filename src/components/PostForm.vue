<template>
 <form @submit.prevent> 
      <h4>Create Post</h4>
      <my-input 
        v-model="post.title"
        type="text"
        placeholder="Title"
      />
      <my-input 
        v-model="post.body"
        type="text"
        placeholder="Descroption"
        />
        <my-button 
          @click="createPost"
          style="align-self: flex-end; margin: 15px;">
          Add new Post
        </my-button>
    </form>
</template>

<script>
import MyButton from '@/components/UI/MyButton'
import MyInput from '@/components/UI/MyInput'
  export default {
    components: {MyButton, MyInput},
    data(){
      return {
        post: {
          title: '',
          body: ''
        }
      }
    },
    methods:{
      createPost(){
        this.post.id = Date.now()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          body: ''
        }
      }
    }
  }
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
}
</style>