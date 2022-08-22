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
        <div class="mx-2 mb-5">
          <button
            v-for="page in pages"
            :key="page.name"
            @click="setID = page.id"
            :class="`w-full text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${
              setID === page.id ? 'bg-light text-white' : 'text-lightest'
            }`"
          >
            <i class="material-icons mr-3">{{ page.icon }}</i>
            <p>{{ page.name }}</p>
          </button>
        </div>
        <div class="mx-5">
          <h1 class="text-xs text-lightest tracking-widest uppercase mb-3">
            Playlists
          </h1>
          <button
            class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2"
          >
            <img
              src="./assets/addNew.png"
              alt="addNew"
              class="h-8 w-8 mr-3 rounded-md"
            />
            <p
              class="text-sm text-white font-semibold transition-all duration-200"
            >
              创建歌单
            </p>
          </button>
          <button
            class="flex items-center justify-start opacity-75 hover:opacity-100"
          >
            <img
              src="./assets/favorites.png"
              alt="favorites"
              class="h-8 w-8 mr-3 rounded-md"
            />
            <p class="text-sm text-white font-semibold transition duration-200">
              已点赞的歌曲
            </p>
          </button>
          <div class="h-px w-full bg-light my-3"></div>
          <div class="mx-1">
            <div class="w-full h-20 overflow-y-scroll">
              <p
                v-for="album in albums"
                :key="album.name"
                class="text-lightest hover:text-white text-sm py-1 transition duration-200"
              >
                {{ album.name }}
              </p>
            </div>
            <button
              class="flex items-center justify-start text-lightest hover:text-white"
            >
              <i class="material-icons mr-2"
                ><span class="material-symbols-outlined">
                  arrow_circle_down
                </span></i
              >
              <p class="text-sm font-semibold">Install App</p>
            </button>
          </div>
        </div>
        <div class="relative pt-11">
          <div
            class="w-full h-full flex justify-end items-start opacity-0 hover:opacity-100 p-2 absolute"
          >
            <div class="bg-black rounded-full h-6 w-6">
              <i class="material-symbols-outlined text-white">
                keyboard_arrow_down
              </i>
            </div>
          </div>
          <img src="./assets/BETTER LATE THAN NEVER .jpg" alt="album-cover" />
        </div>
      </div>
      <!-- main content -->
      <div class="w-full h-full relative">
        <!-- header -->
        <div
          class="v-full sticky top-0 py-4 px-6 flex items-center justify-between"
        >
          <div class="flex items-center">
            <button class="rounded-full bg-black w-9 h-9 text-white mr-3">
              <i class="material-icons text-3xl"> keyboard_arrow_left </i>
            </button>
            <button class="rounded-full bg-black w-9 h-9 text-white">
              <i class="material-icons text-3xl"> keyboard_arrow_right </i>
            </button>
          </div>
          <div class="relative">
            <button
              @click="showDropdown = true"
              class="bg-light rounded-full p-1 px-2 flex items-center"
            >
              <img
                class="rounded-full h-6 w-6"
                src="./assets/avater.jpg"
                alt="avater"
              />
              <p class="text-white font-semibold text-xs mr-1">十月之水</p>
              <i
                v-if="showDropdown === false"
                class="material-icons text-white"
              >
                arrow_drop_down
              </i>
              <i v-if="showDropdown === true" class="material-icons text-white">
                arrow_drop_up
              </i>
            </button>
            <div
              v-if="showDropdown === true"
              class="absolute bg-light w-full rounded mt-1"
            >
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                账户
              </button>
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                个人资料
              </button>
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                支持
              </button>
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                设置
              </button>
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                下载
              </button>
              <button
                @click="showDropdown = false"
                class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
              >
                退出
              </button>
            </div>
          </div>
        </div>
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
        { id: "home", name: "主页", icon: "home" },
        { id: "search", name: "搜索", icon: "search" },
        { id: "library", name: "资料库", icon: "bar_chart" },
      ],
      setID: "home",
      albums: [{ name: "我的歌单" }, { name: "生命之光" }],
      showDropdown: false,
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

.material-symbols-outlined {
  font-variation-settings: "FILL" 0, "wght" 400, "GRAD" 0, "opsz" 48;
}
</style>
