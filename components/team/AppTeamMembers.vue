<template>
  <div class="team pt-100 pb-70">
    <div class="container">
      <div class="section-title text-center">
        <span class="sp-color2">Our Team</span>
        <h2>Our Team Members</h2>
      </div>
      <div class="row pt-45 team" v-if="team.teams.length >= 1">
        <div
          v-for="member in team.teams"
          :key="member.id"
          class="col-sm-6 col-md-4 projects-col"
        >
          <div class="card">
            <div class="thumb">
              <img :src="member.image" alt="" />
              <div class="rollover"></div>
            </div>
            <div class="content">
              <h4>{{ member.name }}</h4>
              <h5>{{ member.job }}</h5>
              <h6>
                {{ member.description.substring(0, 200) }}
                {{ member.description.length > 200 ? "..." : "" }}
              </h6>
              <h5>{{ member.phone }}</h5>
              <h5>{{ member.email }}</h5>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppTeamMembers",
  props: ["team"],
};
</script>

<style lang="scss">
.team-area .section-title {
  margin-bottom: 0;
}
.team-area .section-title span {
  margin-bottom: 8px;
  font-weight: 600;
  display: block;
  color: #f86011;
}
.team-area .section-title h2 {
  max-width: 600px;
  color: #252525;
  font-size: 35px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 42px;
  text-align: left;
  margin-top: 10px;
  margin-right: auto;
  margin-bottom: 15px;
  margin-left: auto;
  text-align: center;
}
.thumb {
  display: flex;
  justify-content: center;
  img {
    margin-top: 20px;
  }
}
.team-area .section-title .seprator img {
  width: 70px;
  margin-top: 5px;
  margin-bottom: 20px;
}
.team-section {
  padding: 30px;
}
.slider-container {
  position: relative;
}
.slider-container .team {
  background: #fff;
}
.slider-container .team .owl-item {
  padding: 50px 50px;
}

.overview-icon {
  height: 34px !important;
}
.overview-icon .one {
  position: static !important;
  font-size: 23px !important;
  text-align: center;
}
.team img {
  border-radius: 50%;
  width: 150px;
  margin-bottom: 30px;
  animation: border-transform 15s infinite ease-in-out;
}
.team .content h4 {
  color: var(--main-color);
  font-size: 20px;
  margin-bottom: 10px;
  letter-spacing: 1px;
  text-transform: uppercase;
}
.team .content h5 {
  color: var(--main-color);
  font-size: 16px;
  margin-bottom: 20px;
  letter-spacing: 1px;
  text-transform: uppercase;
}
.team .content h6 {
  color: #989898;
  font-family: "Open Sans", sans-serif;
  font-size: 14px;
  text-transform: uppercase;
  margin-bottom: 15px;
  line-height: 28px;
  letter-spacing: 0.3px;
}
.team .content h5 {
  color: var(--main-color);
  font-size: 16px;
  margin-bottom: 20px;
  letter-spacing: 1px;
  text-transform: uppercase;
}
.team .content h3 {
  color: var(--main-color);
  font-size: 16px;
  margin-bottom: 20px;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.team .owl-theme .owl-nav .owl-next,
.team .owl-theme .owl-nav .owl-next:hover,
.team .owl-theme .owl-nav .owl-prev,
.team .owl-theme .owl-nav .owl-prev:hover {
  background-color: transparent;
  display: inline-block;
  border-radius: 30px;
  bottom: 0;
  text-align: center;
  line-height: 26px;
  font-size: 20px;
  position: absolute;
  padding: 4px 11px;
  border: 1px solid var(--main-color);
  color: var(--main-color);
}
.team .owl-theme .owl-nav .owl-next:hover,
.team .owl-theme .owl-nav .owl-prev:hover {
  background: var(--main-color);
  color: #fff;
  transition: all 0.2s linear;
}
.team .owl-theme .owl-nav .owl-next {
  right: 45% !important;
}
.team .owl-theme .owl-nav .owl-prev {
  right: 50% !important;
}
.team-area .section-title {
  margin-bottom: 0;
}
.team-area .section-title span {
  margin-bottom: 8px;
  font-weight: 600;
  display: block;
  color: #f86011;
}
.team-area .section-title h2 {
  max-width: 600px;
  color: #252525;
  font-size: 35px;
  font-weight: 800;
  letter-spacing: -1px;
  line-height: 42px;
  text-align: left;
  margin-top: 10px;
  margin-right: auto;
  margin-bottom: 15px;
  margin-left: auto;
  text-align: center;
}
.card {
  padding: 10px 20px;
  text-align: center !important;
}
.team-area .section-title .seprator img {
  width: 70px;
  margin-top: 5px;
  margin-bottom: 20px;
}
</style>
