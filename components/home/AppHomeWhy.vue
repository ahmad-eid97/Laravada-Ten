<template>
  <section class="about-sec">
    <div class="container">
      <div class="row">
        <div class="section-title">
          <h2>WHY WORK WITH US</h2>
        </div>
      </div>
      <div class="row gy-4 justify-content-center align-items-center">
        <div class="col-md-6">
          <div
            class="aboutus right"
            v-if="
              features.find((one) => one.key === 'features_text_list').value
            "
          >
            <h3>5 MAIN REASONS TO CHOOSE US</h3>
            <div
              v-for="(feature, index) in features.find(
                (one) => one.key === 'features_text_list'
              ).value"
              :key="index"
              class="about-item mb-20"
            >
              <div class="about-icon">
                <i :class="`fa-solid fa-${index + 1}`"></i>
              </div>
              <div class="about-details">
                <p>{{ feature.description }}</p>
              </div>
            </div>
          </div>
        </div>

        <div class="col-md-6">
          <div class="about-us">
            <div class="about-us-list">
              <div
                class="about-us-icon-a about-us-icon"
                :class="show == 'show1' ? 'active' : ''"
              >
                <h4 class="one" @click="showData('show1')">
                  <i class="fa-solid fa-user-tie"></i>
                </h4>
              </div>
              <div
                class="about-us-icon-b about-us-icon"
                :class="show == 'show2' ? 'active' : ''"
              >
                <h4 class="one" @click="showData('show2')">
                  <i class="fa-solid fa-gears"></i>
                </h4>
              </div>
              <div
                class="about-us-icon-c about-us-icon"
                :class="show == 'show3' ? 'active' : ''"
              >
                <h4 class="one" @click="showData('show3')">
                  <i class="fa-solid fa-comments"></i>
                </h4>
              </div>
              <div
                class="about-us-icon-d about-us-icon"
                :class="show == 'show4' ? 'active' : ''"
              >
                <h4 class="one" @click="showData('show4')">
                  <i class="fa-solid fa-flag"></i>
                </h4>
              </div>
              <div
                class="about-us-icon-e about-us-icon"
                :class="show == 'show5' ? 'active' : ''"
              >
                <h4 class="one" @click="showData('show5')">
                  <i class="fa-solid fa-briefcase"></i>
                </h4>
              </div>
            </div>
            <div
              class="about-us-main"
              v-if="
                features.find((one) => one.key === 'features_text_list').value
              "
            >
              <h4
                v-for="(feature, index) in features
                  .find((one) => one.key === 'features_text_list')
                  .value.slice(0, 5)"
                :key="index"
                class="about-us-main-icon"
              >
                <div
                  v-if="show == `show${index + 1}`"
                  class="about-us-main-content"
                >
                  <i class="fa-solid fa-user-tie"></i>
                  <h2>
                    {{ feature.title }}
                  </h2>

                  <h3>
                    {{ feature.description }}
                  </h3>
                </div>
              </h4>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AppHomeWhy",
  props: ["features"],
  components: {},
  data() {
    return {
      show: "show1",
    };
  },
  mounted() {
    this.autoPlay();

    document
      .querySelector(".about-sec")
      .style.setProperty(
        "--features-bg",
        this.features.find(
          (one) => one.key === "features_background_active_section"
        ).value === "color"
          ? this.features.find(
              (one) => one.key === "features_background_color_section"
            ).value
          : `url(${
              this.features.find(
                (one) => one.key === "features_background_image_section"
              ).value
            })`
      );

    document
      .querySelector(".about-sec")
      .style.setProperty(
        "--features-fontSize",
        `${
          this.features.find((one) => one.key === "features_font_size_section")
            .value
        }px`
      );

    if (
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ) &&
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ).value === "both"
    ) {
      document
        .querySelector(".about-sec")
        .style.setProperty(
          "--features-border-top",
          `${
            this.features.find(
              (one) => one.key === "features_border_size_section"
            ).value
          }px ${
            this.features.find(
              (one) => one.key === "features_border_type_section"
            ).value
          } ${
            this.features.find(
              (one) => one.key === "features_border_color_section"
            ).value
          }`
        );

      document
        .querySelector(".about-sec")
        .style.setProperty(
          "--features-border-bottom",
          `${
            this.features.find(
              (one) => one.key === "features_border_size_section"
            ).value
          }px ${
            this.features.find(
              (one) => one.key === "features_border_type_section"
            ).value
          } ${
            this.features.find(
              (one) => one.key === "features_border_color_section"
            ).value
          }`
        );
    } else if (
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ) &&
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ).value === "top"
    ) {
      document
        .querySelector(".about-sec")
        .style.setProperty(
          "--features-border-top",
          `${
            this.features.find(
              (one) => one.key === "features_border_size_section"
            ).value
          }px ${
            this.features.find(
              (one) => one.key === "features_border_type_section"
            ).value
          } ${
            this.features.find(
              (one) => one.key === "features_border_color_section"
            ).value
          }`
        );
    } else if (
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ) &&
      this.features.find(
        (one) => one.key === "features_border_position_section"
      ).value === "bottom"
    ) {
      document
        .querySelector(".about-sec")
        .style.setProperty(
          "--features-border-bottom",
          `${
            this.features.find(
              (one) => one.key === "features_border_size_section"
            ).value
          }px ${
            this.features.find(
              (one) => one.key === "features_border_type_section"
            ).value
          } ${
            this.features.find(
              (one) => one.key === "features_border_color_section"
            ).value
          }`
        );
    }
  },
  methods: {
    autoPlay() {
      var items = ["show1", "show2", "show3", "show4", "show5"];
      var item = "";
      let _this = this;
      setInterval(function () {
        item = items[Math.floor(Math.random() * items.length)];
        _this.showData(item);
      }, 5000);
    },
    showData(show) {
      this.show = show;
    },
  },
};
</script>

<style lang="scss">
.about-sec {
  padding: 30px;

  --features-bg: #fff;
  --features-fontSize: 20px;
  --features-border-top: 0px solid #fff;
  --features-border-bottom: 0px solid #fff;

  background: var(--features-bg);
  border-top: var(--features-border-top);
  border-bottom: var(--features-border-bottom);
  background-repeat: no-repeat;
  background-size: cover;
  h2 {
    font-size: var(--features-fontSize);
  }
}
.about-icon {
  display: inline-block;
  border: 3px solid var(--main-color);
  border-radius: 50px;
  display: grid;
  place-content: center;
  font-size: 0.8rem;
  width: 30px !important;
  height: 30px !important;
  i {
    width: 30px !important;
    height: 30px !important;
    display: grid;
    place-content: center;
  }
}
.about-us {
  height: 442px !important;
  width: 452px !important;
  max-width: 450px !important;
  border: 5px solid rgb(231, 231, 231) !important;
  @include xs {
    height: 300px !important;
    width: 300px !important;
  }
}
.about-us .one {
  font-size: 25px !important;
  padding: 5px !important;
}
.about-us-icon {
  background-color: var(--main-color) !important;
}
.about-us-icon-a {
  top: -220px !important;
  @include xs {
    top: -150px !important;
  }
}
.about-us-icon-b {
  left: 210.743px !important;
  @include xs {
    left: 130.743px !important;
  }
}
.about-us-icon-c {
  left: 125.191px !important;
  top: 182.074px !important;
  @include xs {
    left: 110.191px !important;
    top: 92.074px !important;
  }
}
.about-us-icon-d {
  left: -125.191px !important;
  top: 182.074px !important;
  @include xs {
    left: -110.191px !important;
    top: 95.074px !important;
  }
}
.about-us-icon-e {
  left: -210.743px !important;
  @include xs {
    left: -130.743px !important;
  }
}

.about-us-icon .one {
  padding: 9px !important;
  margin: 0 !important;
}
.about-us-icon.active::after {
  content: "";
  position: absolute;
  z-index: -1;
  top: 0;
  right: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: transparent;
  border: 1px solid var(--main-color);
  border-radius: 50px;
  -webkit-animation: ripple 2s infinite ease-in-out;
  animation: ripple 2s infinite ease-in-out;
}
.about-us-main {
  background-color: var(--main-color) !important;
  color: #fff !important;
}
.about-us-main-icon {
  margin-top: 50px;
  @include xs {
    margin: 0;
  }
}
.aboutus {
  h3 {
    /* display: flex; */
    justify-content: flex-end;
    margin-bottom: 30px;
  }
}
.about-item {
  display: flex;
  gap: 10px;
  /* justify-content: flex-end; */
}
@keyframes circle_pop {
  0%,
  100% {
    transform: scale3d(1, 1, 1);
  }
  50% {
    transform: scale3d(1.3, 1.3, 1.3);
  }
}
</style>
