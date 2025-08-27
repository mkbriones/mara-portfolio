<template>
  <div
    :class="{ 'bg-white': !nightMode, 'bg-dark': nightMode }"
    class="pb-5 p-st"
  >
    <div
      class="container"
      data-aos="fade"
      data-aos-once="true"
      data-aos-duration="1000"
    >
      <div class="row align-items-center">
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 text-center">
          <img :src="picture" />
        </div>
        <div class="col-xl-6 col-bg-6 col-md-6 col-sm-12 pt-5">
          <span
            class="home-title"
            :class="{ pgray: !nightMode, 'text-light': nightMode }"
            >{{ name }}</span
          >
          <div>
            <p v-html="description"></p>
          </div>
          <!-- Contact Details Section -->
          <div class="contact-details mt-4 mb-4">
            <div class="contact-item">
              <i class="fa fa-map-marker-alt"></i> <span>{{ location }}</span>
            </div>
            <div class="contact-item">
              <i class="fa fa-phone"></i> <span>{{ phone }}</span>
            </div>
            <div class="contact-item">
              <i class="fa fa-envelope"></i> <span>{{ email }}</span>
            </div>
          </div>
          <div class="pb-4">
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('linkedin')"
              v-tooltip.bottom="'LinkedIn'"
            >
              <i class="fab fa-linkedin"></i>
            </button>
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('facebook')"
              v-tooltip.bottom="'Facebook'"
            >
              <i class="fab fa-facebook"></i>
            </button>
            <button
              class="btn btn-outline-secondary mx-2"
              @click="open('instagram')"
              v-tooltip.bottom="'Instagram'"
            >
              <i class="fab fa-instagram"></i>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import info from "../../info";

import Wave from "./helpers/Wave";

export default {
  name: "Home",
  components: {
    Wave,
  },
  props: {
    nightMode: {
      type: Boolean,
    },
  },
  data() {
    return {
      picture: info.flat_picture,
      name: info.name,
      description: info.description,
      phone: info.details.phone,
      email: info.details.email,
      location: info.details.location,
      linkedin: info.links.linkedin,
      facebook: info.links.facebook,
      instagram: info.links.instagram
    };
  },
  methods: {
    open(link) {
      switch (link) {
        case "linkedin":
          window.open(this.linkedin, "_blank");
          break;
        case "facebook":
          window.open(this.facebook, "_blank");
          break;
        case "instagram":
          window.open(this.instagram, "_blank");
          break;
      }
    },
  },
};
</script>

<style scoped>
.home-title {
  font-size: 28px;
  font-weight: 500;
}

img {
  max-width: 300px;
  margin-top: 60px;
}

@media only screen and (max-width: 580px) {
  img {
    object-fit: cover;
    border-radius: 50%;
    height: 200px;
    width: 200px;
    margin-top: 10px;
    margin-bottom: 10px;
    border: 2px solid rgb(205, 205, 205);
  }
}

.fa {
  font-size: 15px;
}

.btn {
  border-color: #669db3ff;
  color: #669db3ff;
}

.btn:hover {
  background-color: #669db3ff;
  border-color: #669db3ff;
  color: white;
}

.btn:focus {
  background-color: #669db3ff;
  border-color: #669db3ff;
  color: white;
}

.btn:focus {
  outline: none !important;
}

p {
  text-align: justify;
  font-weight: 400;
}

.contact-details {
  margin-top: 20px;
}

.contact-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.contact-item i {
  margin-right: 10px;
}

</style>
