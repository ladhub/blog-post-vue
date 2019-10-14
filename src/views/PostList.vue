<template>
  <div class="post-list">
    <div
      class="card mb-3"
      v-for="data of posts"
      :key="data.id"
      @dblclick="$emit('del-post', data.id)"
    >
      <div class="card-body">
        <h3>
          <router-link :to="`/post-details/${data.id}`">{{data.title}}</router-link>
        </h3>
        <p>{{data.body}}</p>
      </div>
    </div>
    <div class="card mb-3" v-if="errors && errors.length">
      <div class="card-body">
        <p v-for="(error, index) of errors" :key="index">{{error.message}}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from "vue-property-decorator";

@Component({
  name: "PostList"
})
export default class PostList extends Vue {
  private errors: any = [];

  @Prop() private posts: any;
}

// export default {
//     name: "PostList",
//     props: ["posts"],
//     data(){
//         return{
//             errors: []
//         }
//     }
// }
</script>

<style>
</style>