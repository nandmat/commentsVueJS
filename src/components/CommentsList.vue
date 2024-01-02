<template>
  <div class="form-todo form-group">
    <p>
      <input
        type="text"
        placeholder="write your name"
        name="author"
        class="form-control"
        v-model="name"
      />
    </p>
    <p>
      <input
        type="text"
        placeholder="write your message"
        class="form-control"
        v-model="message"
      />
    </p>
    <p class="text-center">
      <button v-on:click="addComment" class="btn btn-success">Comment</button>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      let comment = {
        name: this.name,
        message: this.message,
      };
      if (comment.message.trim() === "") {
        return;
      }
      this.$emit("add-todo", {
        name: this.name,
        message: this.message,
      });
    },
  },
};
</script>

<style>
.form-control {
  border: #f04a30 1px solid;
}

.btn-success {
    background-color: #f04a30;
    border: #f04a30 1px solid;
}
.btn-success:hover {
    background-color: #e7624e;
    border: #e7624e 1px solid;
}
</style>