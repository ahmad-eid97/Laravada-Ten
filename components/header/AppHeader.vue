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
          <b-navbar-nav class="align-items-center">
            <b-nav-item
              active-class="active"
              :to="localePath(`/${item.link}`)"
              exact
              v-for="item in $store.state.topMenu"
              :key="item.id"
            >
              <span v-if="!item.child.length">{{ item.label }}</span>

              <b-dropdown
                :text="item.label"
                block
                class="m-2 dropdownBtn"
                v-if="item.child.length"
              >
                <b-dropdown-item
                  v-for="child in item.child"
                  :key="child.id"
                  :to="localePath('/' + child.link)"
                  >{{ child.label }}</b-dropdown-item
                >
              </b-dropdown>
            </b-nav-item>
            <b-nav-item
              v-if="$store.state.user"
              @click="logout"
              class="outLarge"
            >
              Logout
            </b-nav-item>
          </b-navbar-nav>
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
      this.$swal({
        title: "Logout!",
        text: "Are you sure? You want to logout from your account!",
        type: "warning",
        showCancelButton: true,
        confirmButtonColor: "#ff5e57",
        confirmButtonText: "Logout",
      }).then((result) => {
        if (result.value) {
          this.confirmLogout();
        }
      });
    },
    confirmLogout() {
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
.swal2-container {
  padding: 0 !important;
}
.swal2-shown {
  padding: 0 !important;
}
.swal2-confirm:focus,
.swal2-cancel:focus {
  box-shadow: none !important;
}
.swal2-cancel {
  background: #e5e5e5 !important;
  color: rgb(51, 51, 51) !important;
}
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
  padding: 10px 20px !important;
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
.dropdownBtn {
  margin: 0 !important;
  button {
    background: none !important;
    padding: 0 !important;
    text-transform: none !important;
    font-size: 1.2rem !important;
    font-family: unset !important;
    font-weight: 700 !important;
    box-shadow: none !important;
    border: none !important;
    min-width: 60px !important;
    position: relative;
    top: -3px;
    color: #000;
    &:hover {
      color: var(--main-color) !important;
    }
  }
  .dropdown-menu {
    top: 40px !important;
  }
}
</style>
