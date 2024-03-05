<template>
  <div class="app">
    <h1>Page with Posts</h1>
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
export default {
  components: {
    PostForm, PostList
  },  
  data(){
    return {
      posts: [
        {id: 1, title: 'Title 1',  body: 'body 1'},
        {id: 2, title: 'Title 2',  body: 'body 2'},
        {id: 3, title: 'Title 3',  body: 'body 3'},
      ],
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