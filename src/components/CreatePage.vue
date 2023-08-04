<template>
  <div class="container mb-3">
    <form action="">
      <div class="row">
        <div class="col-8">
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
              v-model="content"
            ></textarea>
          </div>
        </div>
        <div class="col-4">
          <div class="mb-3">
            <label for="" class="form-label"> Link Text </label>
            <input type="text" class="form-control" v-model="linkText" />
          </div>
          <div class="mb-3">
            <label for="" class="form-label"> Link Url </label>
            <input type="text" class="form-control" v-model="linkUrl" />
          </div>
          <div class="mb-3">
            <div class="form-check">
              <input
                type="checkbox"
                class="form-check-input"
                v-model="published"
              />
              <label for="" class="form-check-label">Publish</label>
            </div>
          </div>
        </div>
        <div class="mb-3">
          <button
            :disabled="isFormInvalid"
            class="btn btn-primary"
            @click.prevent="submitForm"
          >
            Create Page
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ["pageCreated"],
  computed: {
    isFormInvalid() {
      return (
        !this.pageTitle || !this.content || !this.linkText || !this.linkUrl
      );
    },
  },
  data() {
    return {
      pageTitle: "",
      content: "",
      linkText: "",
      linkUrl: "",
      published: false,
    };
  },
  methods: {
    submitForm(e) {
      if (!this.pageTitle || !this.content || !this.linkText || !this.linkUrl) {
        alert("Please fill the form!");
        return;
      }

      this.pageCreated({
        pageTitle: this.pageTitle,
        content: this.content,
        link: {
          text: this.linkText,
          url: this.linkUrl,
        },
        published: this.published,
      });

      this.pageTitle = "";
      this.content = "";
      this.linkText = "";
      this.linkUrl = "";
      this.published = false;
    },
  },
};
</script>
