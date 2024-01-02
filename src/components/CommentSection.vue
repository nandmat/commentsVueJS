<template>
  <div class="container">
    <br>
    <div class="d-flex justify-content-between align-items-center">
        <h1 class="h1 text-center">Comments</h1>
        <img src="../assets/comment.png" alt="" width="50px" style="border-radius: 50px;">
    </div>
    <hr style="color:#F04A30;" />
    <CommentsList v-on:add-todo="addComment"></CommentsList>
    <hr style="color:#F04A30;" />
    <div class="list-group text-center">
       <p class="h5" v-if="comments.length == 0">Sem comentários</p>
      <div
        class="list-group-item"
        v-for="(comment, index) in allComments"
        :key="index"
      >
        <span class="comment__author"
          >Author: <strong>{{ comment.name }}</strong>
        </span>
        <p>{{ comment.message }}</p>
        <div>
          <a
            href="#"
            title="Delete"
            class="btn btn-danger"
            v-on:click.prevent="removeComment(index)"
            >Delete</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import CommentsList from './CommentsList.vue';
export default {

  components: {
    CommentsList, 
  },

  data() {
    return {
      comments: [],
      name: "",
      message: "",
    };
  },
  methods: {
    addComment(comment){
        this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        comment,
        name: comment.name.trim() === "" ? "Anonymous" : comment.name,
      }));
    },
  },
  watch: {
    comments(value) {
      console.log(value);
    },
  },
};
</script>

<style>
.list-group-item {
    border-color: #e7624e;
}
</style>
