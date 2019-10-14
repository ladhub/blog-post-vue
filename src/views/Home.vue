<template>
  <div class="home">
    <AddPost v-on:add-post="addPost" />
    <PostList v-bind:posts="posts" v-on:del-post="deletePost" />
  </div>
</template>

<script lang='ts'>
// @ is an alias to /src

import { Vue, Component, Prop } from "vue-property-decorator";
import axios from "axios";
import AddPost from "@/views/AddPost.vue";
import PostList from "@/views/PostList.vue";

@Component({
  name: "home",
  components: {
    AddPost,
    PostList
  }
})
export default class Home extends Vue {
  private posts: any = [];
  private err: any = [];

  private addPost(newPost: any): void {
    const { title, body } = newPost;
    axios
      .post("https://jsonplaceholder.typicode.com/posts", {
        title,
        body
      })
      .then(response => (this.posts = [...this.posts, response.data]))
      .catch(err => console.log(err));
  }

  private deletePost(id: any): void {
    axios
      .delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(() => {
        this.posts = this.posts.filter((post: any) => post.id !== id);
      })
      .catch(err => {
        console.log(err);
      });
  }

  private created(): void {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts?_limit=5`)
      .then(response => {
        this.posts = response.data;
      })
      .catch(err => {
        console.log(err);
      });
  }
}

// export default {
//   name: 'home',
//   components: {
//     AddPost,
//     PostList
//   },
//   data(){
//     return{
//       posts: [],
//       errors: []
//     }
//   },
//   methods: {
//     addPost(newPost){
//       const {title, body} = newPost;
//       axios.post("https://jsonplaceholder.typicode.com/posts", {
//         title,
//         body
//       })
//       .then(response => (this.posts = [...this.posts, response.data]))
//       .catch(
//         err => console.log(err)
//       )
//     },
//     deletePost(id){
//       console.log('asdfsdf')
//       axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
//       .then( () => {
//         this.posts = this.posts.filter(post => post.id !== id)
//       })
//       .catch(err => {
//         console.log(err);
//       })
//     }
//   },
//   created(){
//     axios.get(`https://jsonplaceholder.typicode.com/posts?_limit=5`)
//     .then(response => {
//       this.posts = response.data
//     })
//     .catch(err => {
//         console.log(err);
//       })
//   }
// }
</script>
