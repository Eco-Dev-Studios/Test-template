<template>
  <div class="h-auto w-full">
    <!--Header-->
    <app-header></app-header>
    <!--Index-->

    <app-layout size="xl" class="pt-18">
      <main class="h-screen w-full relative">
        <div class="animate-animated animate-fade-in w-1/2 center-y">
          <h1 class="font-bold font-sans mb-4 text-7xl text-gray-900">
            Landing Page <br />
            Template
          </h1>
          <p
            class="font-sans font-semibold text-xl text-gray-900 text-opacity-70"
          >
            To facilitate the creation of landing pages, one pages or
            portfolios, this project gives us the necessary configuration tools
            to start a project without much need.
          </p>
          <small class="font-semibold text-gray-900"
            >By Eco Development Studios</small
          >
        </div>
      </main>
    </app-layout>
  </div>
</template>

<script>
export default {
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll(event) {
      this.scrollY = window.scrollY;
      this.$store.commit("scroll/setPosition", window.scrollY);
      this.$store.commit("scroll/isInViewport", "section2");
    },
  },
  computed: {
    getMode() {
      let nuxtLogo = "";
      if (this.$colorMode.preference === "light") {
        nuxtLogo = "nuxt-logo.svg";
      }
      if (this.$colorMode.preference === "dark") {
        nuxtLogo = "nuxt-logo-dark.svg";
      }
      return nuxtLogo;
    },
    getScroll() {
      return this.$store.state.scroll.scrollY;
    },
    isInViewport() {
      return this.$store.state.scroll.isInViewport;
    },
  },
  head: {
    title: "Home Page",
    meta: [
      {
        hid: "home",
        name: "home",
        content: "We are a studio that design and develop to the web",
      },
    ],
  },
};
</script>
