<template>
  <div class="post-details">
    <div class="row mb-3">
      <div class="col-auto">
        <router-link class="btn btn-block btn-info" to="/">Go Back</router-link>
      </div>
    </div>
    <div class="card bg-dark mb-3">
      <div class="card-body">
        <h3>{{post.title}}</h3>
        <p>{{post.body}}</p>
      </div>
    </div>
    <PostComments />
  </div>
</template>

<script lang="ts">
import axios from "axios";
import PostComments from "./PostComments.vue";
import { Vue, Component, Prop } from "vue-property-decorator";

interface IPostDetails {
  userId?: number;
  id?: number;
  title?: string;
  body?: string;
}

@Component({
  name: "PostDetails",
  components: {
    PostComments
  }
})
export default class PostDetails extends Vue {
  private post: IPostDetails = {};
  private errors: any = [];
  private title: string = "";
  private body: string = "";

  private created(): void {
    axios
      .get(
        "https://jsonplaceholder.typicode.com/posts/" + this.$route.params.id
      )
      .then(response => {
        this.post = response.data || {};
      })
      .catch(errors => console.log(errors));
  }
}

// export default {
//     name: "PostDetails",
//     components:{
//         PostComments,
//     },
//     data() {
//         return {
//             id: this.$route.params.id,
//             post:[]
//         }
//     },
//     created(){
//     axios
//         .get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
//         .then(response => {
//             this.post = response.data
//         })
//         .catch(e =>{
//             this.errors.push(e);
//         })
//   }
// }
</script>

<style>
</style>