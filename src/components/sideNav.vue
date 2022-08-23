<template>
  <div class="w-56 bg-black h-full flex-none">
    <div class="p-6">
      <img
        src="../assets/logo/Spotify_Logo_RGB_White.png"
        class="h-10"
        alt="spotify-logo"
      />
    </div>
    <div class="mx-2 mb-5">
      <button
        v-for="page in pages"
        :key="page.name"
        @click="setid = page.id"
        :class="`w-full text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${
          setid === page.id ? 'bg-light text-white' : 'text-lightest'
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
        class="transition duration-400 flex items-center justify-start opacity-75 hover:opacity-100 mb-2"
      >
        <img
          src="../assets/addNew.png"
          alt="addNew"
          class="h-8 w-8 mr-3 rounded-md"
        />
        <p class="text-sm text-white font-semibold transition-all duration-200">
          创建歌单
        </p>
      </button>
      <button
        class="transition duration-400 flex items-center justify-start opacity-75 hover:opacity-100"
      >
        <img
          src="../assets/favorites.png"
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
          <p class="text-sm font-semibold">安装应用</p>
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
      <img src="../assets/BETTER LATE THAN NEVER .jpg" alt="album-cover" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      setid: this.setID,
    };
  },
  props: ["pages", "setID", "albums"],
};
</script>

<style></style>
