<template>
  <div>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, `navbar navbar-expand-lg`]">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Vue 3</a>
        <button
          class="navbar-toggler"
          type="button"
          data-toggle="collapse"
          data-target="#navbarText"
          aria-controls="navbarText"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarText">
          <ul class="navbar-nav me-auto">
            <li
              v-for="(page, index) in pages"
              class="nav-item active"
              :key="index"
            >
              <a
                class="nav-link"
                :class="{ active: activePage == index }"
                :title="`This link goes to ${page.link.text} page`"
                :href="page.link.url"
                @click.prevent="navLinkClick(index)"
                >{{ page.link.text }}
              </a>
            </li>
          </ul>

          <form class="d-flex">
            <button class="btn btn-primary" @click.prevent="changeTheme()">
              Toggle
            </button>
          </form>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  props: ["pages", "activePage", "navLinkClick"],

  data() {
    return {
      theme: "light",
    };
  },

  methods: {
    changeTheme() {
      let theme = "light";

      if (this.theme == "light") {
        theme = "dark";
      }
      this.theme = theme;
    },
  },
};
</script>
