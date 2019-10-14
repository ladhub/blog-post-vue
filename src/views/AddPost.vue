<template>
  <div class="add-post">
    <div class="row mb-3">
      <div class="col text-right">
        <button class="btn btn-primary" v-on:click="formShow">Create New Post</button>
      </div>
    </div>
    <div class="card bg-dark mb-3" v-if="formDiv">
      <div class="card-body">
        <form @submit.prevent="addPost">
          <div class="form-group">
            <label for>Post Title</label>
            <input
              v-model="title"
              type="text"
              name="title"
              class="form-control"
              placeholder="Enter post  title"
            />
          </div>
          <div class="form-group">
            <label for>Post Details</label>
            <textarea
              v-model="body"
              class="form-control"
              name="body"
              placeholder="Enter post details"
            ></textarea>
          </div>
          <div class="row">
            <div class="col-6 mx-auto">
              <button class="btn btn-block btn-success">Create Post</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component
export default class AddPost extends Vue {
  private formDiv: boolean = false;
  private title: string = "";
  private body: string = "";

  private formShow(): boolean {
    return (this.formDiv = true);
  }

  private addPost(): void {
    const newPost = {
      title: this.title,
      body: this.body
    };

    //send up to parent
    this.$emit("add-post", newPost);
    (this.title = ""), (this.body = "");
  }
}

// export default {
//   name: "AddPost",
//   data() {
//     return {
//       formDiv: false,
//       title: "",
//       body: ""
//     };
//   },
//   methods: {
//     formShow() {
//       this.formDiv = true;
//     },
//     addPost() {
//       const newPost = {
//         title: this.title,
//         body: this.body
//       };

//       //send up to parent
//       this.$emit("add-post", newPost);
//       (this.title = ""), (this.body = "");
//     }
//   }
// };
</script>

<style>
</style>