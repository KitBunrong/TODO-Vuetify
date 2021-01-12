<template>
  <v-app>
    <Navigation :flat="flat" />
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
import Navigation from "./components/Navigation";
export default {
  data: () => ({
    flat: true,
    lastScrollPosition: 0,
  }),
  components: {
    Navigation,
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll(e) {
      if (typeof window === "undefined") return;
      const top = window.pageYOffset || e.target.documentElement.scrollTop || 0;
      if (top > 40) {
        this.flat = false;
      } else {
        this.flat = true;
      }
    },
  },
};
</script>
