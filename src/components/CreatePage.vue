<template>
  <div class="container mb-3">
    <form action="">
      <div class="mb-3">
        <label for="" class="form-label"> Page Title </label>
        <input type="text" class="form-control" v-model="pageTitle" />
      </div>
      <div class="mb-3">
        <label for="" class="form-label"> Content main </label>
        <textarea
          type="text"
          class="form-control"
          rows="5"
          v-model="pageContent"
        ></textarea>
      </div>
      <div class="mb-3">
        <button
          class="btn btn-primary"
          @click.prevent="pageCreated({ pageTitle, pageContent })"
        >
          Create Page
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ["pageCreated"],
  data() {
    return {
      pageTitle: "",
      pageContent: "",
    };
  },
};
</script>
