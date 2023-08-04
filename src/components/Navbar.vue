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
              <navbar-link
                :page="page"
                :isActive="activePage === index"
                @click.prevent="navLinkClick(index)"
              ></navbar-link>
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
import NavbarLink from "./NavbarLink.vue";

export default {
  components: { NavbarLink },
  props: ["pages", "activePage", "navLinkClick"],

  created() {
    this.getThemeSetting();
  },

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
      this.storeThemeSetting();
    },

    storeThemeSetting() {
      localStorage.setItem("theme", this.theme);
    },

    getThemeSetting() {
      let theme = localStorage.getItem("theme", this.theme);
      if (theme) {
        this.theme = theme;
      }
    },
  },
};
</script>
