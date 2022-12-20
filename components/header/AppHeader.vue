<template>
  <div>
    <app-top-bar></app-top-bar>
    <header class="header header-style-2 clearfix">
      <b-navbar
        toggleable="lg"
        :class="{ onScroll: !topOfPage }"
        class="navbar navbar-expand-lg navbar-light py-0"
      >
        <b-navbar-brand :href="localePath('/')"
          ><img
            src="/assets/images/logo.png"
            alt="logo"
            class="logo"
            style="width: 200px"
        /></b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <ul class="navbar-nav me-auto">
            <li class="nav-item">
              <router-link
                :to="localePath('/')"
                class="nav-link"
                aria-current="page"
                href="#"
              >
                <div class="row m-0 justify-content-center">
                  <i class="fa-solid fa-house"></i>
                  <span> Home </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item dropdown">
              <dropdown-menu
                v-model="show"
                :hover="true"
                :closeOnClickOutside="true"
                :hover_time="10"
              >
                <router-link
                  :to="localePath('/team')"
                  class="nav-link dropdown-toggle"
                  href="http://example.com"
                  id="navbarDropdownMenuLink"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  aria-expanded="false"
                >
                  <div class="row m-0 justify-content-center">
                    <i class="fa-solid fa-users"></i>
                    <span> Company </span>
                  </div>
                </router-link>
                <div slot="dropdown">
                  <a class="dropdown-item" href="#">dropdown link</a>
                  <a class="dropdown-item" href="#">dropdown link</a>
                  <a class="dropdown-item" href="#">dropdown link</a>
                </div>
              </dropdown-menu>
            </li>

            <li class="nav-item dropdown">
              <dropdown-menu
                v-model="show1"
                :hover="true"
                :closeOnClickOutside="true"
                :hover_time="10"
              >
                <router-link
                  :to="localePath('/services')"
                  class="nav-link dropdown-toggle"
                  href="http://example.com"
                  id="navbarDropdownMenuLink"
                  data-toggle="dropdown"
                  aria-haspopup="true"
                  aria-expanded="false"
                >
                  <div class="row m-0 justify-content-center">
                    <i class="fa-solid fa-paste"></i>
                    <span> Services </span>
                  </div>
                </router-link>
                <div slot="dropdown">
                  <a class="dropdown-item" href="#">dropdown link</a>
                  <a class="dropdown-item" href="#">dropdown link</a>
                  <a class="dropdown-item" href="#">dropdown link</a>
                </div>
              </dropdown-menu>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/testimonials')" class="nav-link">
                <div class="row m-0 justify-content-center">
                  <i class="fa-solid fa-folder-open"></i>
                  <span> Projects </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/blogs')" class="nav-link" href="#">
                <div class="row m-0 justify-content-center">
                  <i class="fa-solid fa-bookmark"></i>
                  <span> Blogs </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/careers')" class="nav-link">
                <div class="row m-0 justify-content-center">
                  <i class="fa-solid fa-user-doctor"></i>
                  <span> Career </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/events')" class="nav-link">
                <div class="row m-0 justify-content-center">
                  <i class="fa-regular fa-calendar-days"></i>
                  <span> Events </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link
                :to="localePath('/contact')"
                class="nav-link"
                href="#"
              >
                <div class="row m-0 justify-content-center">
                  <i class="fa-solid fa-envelope"></i>
                  <span> Contact </span>
                </div>
              </router-link>
            </li>
          </ul>

          <div class="btn-container">
            <button class="btn nav-btn fw-bold">
              Start a project <i class="fa-solid fa-circle-arrow-right"></i>
            </button>
          </div>
          <lang-switch></lang-switch>
          <div v-if="$store.state.user" class="logout" @click="logout">
            <i class="fa-regular fa-right-from-bracket"></i>
          </div>
        </b-collapse>
      </b-navbar>
    </header>
  </div>
</template>

<script>
import AppTopBar from "./AppTopBar.vue";
import DropdownMenu from "@innologica/vue-dropdown-menu";
import LangSwitch from "../langSwitch/langSwitch.vue";
export default {
  name: "AppHeader",
  components: {
    AppTopBar,
    DropdownMenu,
    LangSwitch,
  },
  data() {
    return {
      show: false,
      show1: false,
      topOfPage: true,
    };
  },
  beforeMount() {
    window.addEventListener("scroll", this.handleScroll);
  },
  mounted() {},
  methods: {
    logout() {
      this.$store.commit("setUserData", null);
      this.$cookies.remove("cms-auth");
      this.$cookies.remove("cms-user");
      this.$router.push(this.localePath("/login"));
    },
    handleScroll() {
      if (window.pageYOffset > 200) {
        if (this.topOfPage) this.topOfPage = false;
      } else {
        if (!this.topOfPage) this.topOfPage = true;
      }
    },
  },
};
</script>
<style lang="scss">
header {
  padding: 0px 50px;
}
@include md {
  header {
    padding: 10px 50px;
  }
}
.onScroll {
  position: fixed;
  width: 100%;
  display: flex;
  align-items: center;
  transition: all 0.2s ease-in-out;
  box-shadow: 0 0 10px #aaa;
  background-color: #fff;
  top: 0;
  z-index: 10;
  left: 0;
  padding: 0 50px;
}
.logout {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: var(--main-color);
  color: #fff;
  display: grid;
  place-items: center;
  font-size: 1.2rem;
  cursor: pointer;
}
.navbar-nav .nav-link {
  padding: 10px 0 !important;
  font-weight: bold;
  text-align: center;
  font-size: 19px;
  height: 100px;
  display: flex;
  align-items: center;
}
.navbar-nav .nav-link i {
  display: block;
  max-width: 40px;
}
.navbar-nav .nav-link.active,
.navbar-nav .nav-link:hover {
  background-color: rgba(147, 194, 72, 0.15);
  color: var(--main-color) !important;
}
.navbar .dropdown-menu {
  border-radius: 0;
  background-color: #fff;
  padding: 10px;
  width: 280px;
  padding: 10px;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
}
.navbar .dropdown-menu a {
  margin: 0 0 1px;
  padding: 12px;
}
.navbar .dropdown-menu a:hover {
  background-color: rgba(147, 194, 72, 0.15);
  color: var(--main-color) !important;
}
img.logo {
  width: 200px;
}
</style>
