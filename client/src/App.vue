<template>
  <div id="app">
    <Navbar></Navbar>

    <router-view />
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
export default {
  name: "App",
  components: {
    Navbar
  },
  mounted() {
    if (localStorage.getItem("token")) {
      this.$store.commit("changeLogin", true);
    } else {
      this.$store.commit("changeLogin", false);
    }

    if (localStorage.getItem("role") == "admin") {
      this.$router.push("/admin");
    }
  },
  created() {
    if (localStorage.getItem("role") == "admin") {
      this.$router.push("/admin");
    }
  },
  methods: {}
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
