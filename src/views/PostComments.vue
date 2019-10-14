<template>
  <div class="post-comments">
    <div class="card mb-3" v-for="comment in comments" :key="comment.id">
      <div class="row no-gutters">
        <div class="col-md-2">
          <img src="@/assets/logo.png" class="card-img" />
        </div>
        <div class="col-md-10">
          <div class="card-body">
            <h5 class="card-title">{{comment.name}}</h5>
            <p class="card-text">{{comment.body}}.</p>
            <p class="card-text">
              <small class="text-muted">{{comment.email}}</small>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import { Vue, Component, Prop } from "vue-property-decorator";

@Component({
  name: "PostComments"
})
export default class PostComments extends Vue {
  private comments: any = [];
  private errors: any = [];

  private created(): void {
    axios
      .get(
        `https://jsonplaceholder.typicode.com/comments?postId=${this.$route.params.id}`
      )
      .then(resp => {
        console.log("this is from get ", resp);
        this.comments = resp.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
}

// export default {
//     name: "PostComments",
//     data() {
//         return {
//             id: this.$route.params.id,
//             comments: [],
//             errors: []
//         }
//     },
//     created(){
//         axios
//         .get(`https://jsonplaceholder.typicode.com/comments?postId=${this.id}`)
//         .then(resp => {
//             this.comments = resp.data;
//         })
//         .catch(e => {
//             this.errors.push(e);
//             console.log(this.errors)
//         });
//     }
// }
</script>

<style>
</style>