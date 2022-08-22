<template>
  <div class="bg-drak h-screen">
    <div class="flex" style="height: 88vh">
      <!-- side nav -->
      <div class="w-56 bg-black h-full flex-none">
        <div class="p-6">
          <img
            src="./assets/logo/Spotify_Logo_RGB_White.png"
            class="h-10"
            alt="spotify-logo"
          />
        </div>
        <div class="mx-2">
          <button
            v-for="page in pages"
            :key="page.name"
            @click="setID = page.id"
            :class="`w-full text-xs font-semibold rounded px-3 py-2 flex items-center justify-start ${
              setID === page.id ? 'bg-light text-white' : 'text-lightest'
            }`"
          >
            <i class="material-icons">{{ page.icon }}</i>
            <p>{{ page.name }}</p>
          </button>
        </div>
      </div>
      <!-- main content -->
      <div class="w-full h-full relative bg-blue-400">
        <!-- header -->
        <div class="v-full sticky top-0 p-2"></div>
      </div>
    </div>
    <!-- play bar -->
    <div class="w-full bg-light" style="height: 12vh"></div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    return {
      pages: [
        { id: "home", name: "Home", icon: "home" },
        { id: "search", name: "Search", icon: "search" },
        { id: "library", name: "Your Library", icon: "bar_chart" },
      ],
      setID: "home",
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
