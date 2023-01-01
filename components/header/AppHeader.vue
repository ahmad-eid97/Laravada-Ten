<template>
  <div>
    <app-top-bar></app-top-bar>
    <header class="header header-style-2 clearfix">
      <b-navbar
        toggleable="lg"
        :class="{ onScroll: !topOfPage }"
        class="navbar navbar-expand-lg navbar-light py-0"
      >
        <div class="cart" :class="openCart ? 'opened' : ''">
          <div class="head">
            <i class="fa-regular fa-xmark" @click="openCart = false"></i>
            <button
              @click="goToCheckout"
              :disabled="$store.state.cartItems.length <= 0"
            >
              <i class="fa-regular fa-badge-check"></i> Checkout
            </button>
          </div>
          <cart />
        </div>

        <b-navbar-brand :href="localePath('/')" class="brand"
          ><img
            src="/assets/images/logo.png"
            alt="logo"
            class="logo"
            style="width: 200px"
        /></b-navbar-brand>

        <div class="d-flex align-items-center smallScr">
          <lang-switch></lang-switch>
          <div class="m-0 cartIcon" @click="openCart = !openCart">
            <span>{{ $store.state.cartItems.length }}</span>
            <i class="fa-regular fa-cart-plus"></i>
          </div>
          <div v-if="$store.state.user" class="logout" @click="logout">
            <i class="fa-regular fa-right-from-bracket"></i>
          </div>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        </div>

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
                  <!-- <i class="fa-solid fa-house"></i> -->
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
                    <!-- <i class="fa-solid fa-users"></i> -->
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
                    <!-- <i class="fa-solid fa-paste"></i> -->
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
                  <!-- <i class="fa-solid fa-folder-open"></i> -->
                  <span> Projects </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/blogs')" class="nav-link" href="#">
                <div class="row m-0 justify-content-center">
                  <!-- <i class="fa-solid fa-bookmark"></i> -->
                  <span> Blogs </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/careers')" class="nav-link">
                <div class="row m-0 justify-content-center">
                  <!-- <i class="fa-solid fa-user-doctor"></i> -->
                  <span> Career </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item">
              <router-link :to="localePath('/events')" class="nav-link">
                <div class="row m-0 justify-content-center">
                  <!-- <i class="fa-regular fa-calendar-days"></i> -->
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
                  <!-- <i class="fa-solid fa-envelope"></i> -->
                  <span> Contact </span>
                </div>
              </router-link>
            </li>

            <li class="nav-item outLarge">
              <router-link
                :to="localePath('/login')"
                class="nav-link"
                v-if="$store.state.user"
                @click="logout"
              >
                <div class="row m-0 justify-content-center">
                  <!-- <i class="fa-solid fa-envelope"></i> -->
                  <span> Logout </span>
                </div>
              </router-link>
            </li>
          </ul>
        </b-collapse>

        <div class="d-flex align-items-center largeScr">
          <lang-switch></lang-switch>
          <div class="m-0 cartIcon" @click="openCart = !openCart">
            <span>{{ $store.state.cartItems.length }}</span>
            <i class="fa-regular fa-cart-plus"></i>
          </div>
          <div v-if="$store.state.user" class="logout" @click="logout">
            <i class="fa-regular fa-right-from-bracket"></i>
          </div>
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        </div>
      </b-navbar>
    </header>
  </div>
</template>

<script>
import cart from "../cart/cart.vue";
import AppTopBar from "./AppTopBar.vue";
import DropdownMenu from "@innologica/vue-dropdown-menu";
import LangSwitch from "../langSwitch/langSwitch.vue";
export default {
  name: "AppHeader",
  components: {
    AppTopBar,
    DropdownMenu,
    LangSwitch,
    cart,
  },
  data() {
    return {
      show: false,
      show1: false,
      topOfPage: true,
      openCart: false,
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
    goToCheckout() {
      this.openCart = false;
      this.$router.push("/checkout");
    },
  },
};
</script>
<style lang="scss">
header {
  padding: 20px 50px;
  @include md {
    padding: 20px 10px !important;
  }
  .cart {
    width: 390px;
    height: 100vh;
    position: fixed;
    top: 0;
    right: 0;
    transform: translateX(390px);
    background-color: #fff;
    z-index: 999999;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
    .head {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px;
      & > i {
        border: 1px solid var(--main-color);
        border-radius: 5px;
        width: 30px;
        height: 30px;
        display: grid;
        place-items: center;
        cursor: pointer;
        background-color: var(--main-color);
        color: #fff;
        &:hover {
          color: var(--main-color);
          background: transparent;
        }
      }
      button {
        padding: 5px 30px;
        font-size: 1.1rem;
        background-color: var(--main-color);
        color: #fff;
        border: 1px solid var(--main-color);
        display: flex;
        align-items: center;
        gap: 5px;
        i {
          font-size: 1.1rem;
        }
        &:disabled {
          opacity: 0.5;
          cursor: not-allowed;
          &:hover {
            background-color: var(--main-color);
            color: #fff;
          }
        }
        &:hover {
          background-color: transparent;
          color: var(--main-color);
        }
      }
    }
    &.opened {
      transform: translateX(0);
    }
    @include xs {
      width: 350px;
    }
  }
  .cartIcon {
    border: 1px solid var(--main-color);
    border-radius: 5px;
    width: 45px;
    height: 45px;
    display: grid;
    place-items: center;
    cursor: pointer;
    position: relative;
    margin: 0 15px !important;
    span {
      position: absolute;
      top: -15px;
      right: -10px;
      width: 30px;
      height: 30px;
      background-color: var(--main-color);
      border-radius: 50%;
      color: #fff;
      display: grid;
      place-content: center;
      font-size: 1.2rem;
      @include sm {
        font-size: 1rem;
      }
    }
    i {
      color: var(--main-color);
    }
    @include sm {
      width: 40px;
      height: 40px;
      margin: 0 10px !important;
    }
    &:hover {
      background-color: var(--main-color);
      border-color: var(--main-color);
      i {
        color: #fff;
      }
    }
  }
}
@include md {
  header {
    padding: 10px 50px;
  }
}
.outLarge {
  display: none;
  @include md {
    display: inline;
  }
}
.smallScr {
  align-items: center;
  display: none !important;
  @include md {
    display: flex !important;
  }
}
.largeScr {
  align-items: center;
  display: flex !important;
  @include md {
    display: none !important;
  }
}
.brand {
  img {
    @include sm {
      width: 150px !important;
    }
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
  padding: 20px 50px !important;
  @include sm {
    padding: 15px 10px !important;
  }
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
  @include md {
    display: none;
  }
}
.navbar-nav .nav-link {
  padding: 10px 0 !important;
  font-weight: bold;
  text-align: center;
  font-size: 19px;
  /* height: 100px; */
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
