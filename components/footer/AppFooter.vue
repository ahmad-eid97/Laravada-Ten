<template>
  <section class="footer">
    <subscribe />
    <div class="d-flex justify-content-around pt-5 responsive-footer">
      <div class="w-30 mt-2 w-control">
        <img
          class="img-fluid"
          :src="
            $store.state.websiteSettings.find((one) => one.key === 'logo')
              .plain_value
          "
          alt="logo"
          style="width: 250px"
        />
        <p class="text-light my-2 fs-5">
          {{
            $store.state.websiteSettings.find(
              (one) => one.key === "description"
            ).plain_value
          }}
        </p>
        <button class="btn test-btn mt-3" @click="$router.push('/about')">
          Get in touch!
        </button>
      </div>

      <div class="text-light w-30 mt-2 w-control">
        <h5 class="fw-bold mb-4">Contact info</h5>

        <p class="">Phone number</p>
        <p class="footer-text">
          {{
            $store.state.websiteSettings.find(
              (one) => one.key === "contact_phone"
            ).plain_value
          }}
        </p>

        <p class="">Email</p>
        <p class="footer-text">
          {{
            $store.state.websiteSettings.find((one) => one.key === "email")
              .plain_value
          }}
        </p>

        <p class="">Address</p>
        <p class="footer-text">
          {{
            $store.state.websiteSettings.find(
              (one) => one.key === "contact_address"
            ).plain_value
          }}
        </p>

        <div class="d-flex d-none d-lg-flex d-md-none">
          <div class="footer-icon fs-12">
            <i class="fa-brands fa-facebook-f"></i>
          </div>
          <div class="footer-icon fs-12">
            <i class="fa-brands fa-twitter"></i>
          </div>
          <div class="footer-icon fs-12">
            <i class="fa-brands fa-google"></i>
          </div>
        </div>
      </div>

      <div class="w-30 w-control">
        <h5>Other Pages</h5>
        <ul class="footer-list">
          <!-- <li><a href="#">About Us</a></li> -->
          <li v-for="page in $store.state.footerPages" :key="page.id">
            <nuxt-link
              :to="localePath(generatePagePath(page.id))"
              v-if="page.status"
              >{{ page.name }}</nuxt-link
            >
          </li>
        </ul>
      </div>
    </div>

    <div class="footer-border footer-text">
      <img
        :src="
          $store.state.websiteSettings.find((one) => one.key === 'logo')
            .plain_value
        "
        alt="logoImage"
        style="width: 200px"
      />
      <p>© Powered By: Rail Coder - 2022-2023. All rights reserved.</p>
    </div>
  </section>
</template>

<script>
import subscribe from "../../components/subscribe/subscribe.vue";

export default {
  name: "AppFooter",
  components: { subscribe },
  data() {
    return {};
  },
  beforeMount() {},
  methods: {
    generatePagePath(id) {
      switch (id) {
        case 1:
          return "/about";
        case 2:
          return "/contact";
        case 3:
          return "/terms";
        case 4:
          return "/policy";
      }
    },
  },
};
</script>

<style lang="scss">
.footer {
  padding: 0;
}
h5 {
  color: #fff;
}
.footer-list {
  list-style: none;
  padding: 0;
  margin-top: 25px;
  li {
    padding: 5px 0;
    a {
      color: #fff;
    }
  }
}
.footer .btn {
  background-color: var(--main-color);
  border-color: var(--main-color);
  border-radius: 20px;
  color: #fff;
}
.footer-border {
  width: 100% !important;
  background-color: #353b43;
  margin: 30px 0 0 !important;
}
.footer-border p {
  color: #fff;
  margin: 10px 0;
}
</style>
