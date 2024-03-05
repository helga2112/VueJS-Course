<template>
  <div class="app">
    <h1>Page with Posts</h1>
    <my-button @click="fetchPosts" style="margin: 15px;">Get Post</my-button>
    <input type="text" v-model.trim.number="modificatorValue"></input>
    <my-button @click="showDialog" style="margin: 15px;">Add New Post</my-button>
    <my-dialog v-model:show="dialogVisibile">
      <post-form @create="createPost"/>
    </my-dialog>
   
    <post-list 
      :posts="posts"
      @remove="removePost"
      />
    
  </div>

</template>


<script>
import PostForm from '@/components/PostForm'
import PostList from '@/components/PostList'
import axios from 'axios'
export default {
  components: {
    PostForm, PostList
  },  
  data(){
    return {
      posts: [],
    dialogVisibile: false,
    modificatorValue: '',
    }

  },
  methods:{
    createPost(post){
      this.posts.push(post)
      this.dialogVisibile = false
    },
    removePost(post){
      this.posts = this.posts.filter((item) => item.id !== post.id) 
    },
    showDialog(){
      this.dialogVisibile = true
    },

    async fetchPosts(){
      try{
        const resp = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = resp.data
      }catch(e){
        alert('Error: ', e)
      }
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

</style>