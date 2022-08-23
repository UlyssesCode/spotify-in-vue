<template>
  <div
    class="border-t-2 border-dark w-full flex items-center justify-between px-3 bg-light"
    style="height: 12vh"
  >
    <div class="flex items-center">
      <div>
        <h1 class="text-sm text-white tracking- hover:underline">
          一个短篇 A Short Story
        </h1>
        <h2 class="text-xs text-lightest tracking-wide hover:underline">
          相见恨晚
        </h2>
      </div>
      <i class="material-icons text-xl text-green mx-4">favorite</i>
      <i class="material-icons text-xl text-lightest">
        picture_in_picture_alt</i
      >
    </div>
    <div class="flex flex-col justify-center w-2/4 items-center">
      <div class="flex items-center">
        <button class="mx-5 text-lightest hover:text-white">
          <i class="material-icons text-lg">shuffle</i>
        </button>
        <button class="text-lightest hover:text-white">
          <i class="material-icons text-lg">skip_previous</i>
        </button>
        <button
          @click="playSong()"
          class="rounded-full h-10 w-10 flex items-center mx-5 justify-center text-white hover:text-white"
        >
          <i v-if="pause === false" class="material-icons text-2xl"
            >play_circle</i
          ><i v-if="pause === true" class="material-icons text-2xl">pause</i>
        </button>
        <button class="text-lightest hover:text-white">
          <i class="material-icons text-lg">skip_next</i>
        </button>
        <button class="mx-5 text-lightest hover:text-white">
          <i class="material-icons text-lg">repeat</i>
        </button>
      </div>
      <div class="w-3/4 flex items-center mt-3">
        <p class="text-xs text-lightest mr-1">0:28</p>
        <div class="w-full h-1 bg-dark rounded-full flex items-center">
          <div class="h-1 rounded-full bg-green" style="width: 18%"></div>
          <div class="h-3 w-3 bg-white rounded-full shadow"></div>
        </div>
        <p class="text-xs text-lightest mr-1">2:40</p>
      </div>
    </div>
    <div class="flex items-center w-1/4 justify-end">
      <i class="mx-2 material-icons text-xl text-lightest">playlist_play</i>
      <i class="mx-2 material-icons text-xl text-lightest">cast</i>
      <i class="mx-2 material-icons text-xl text-lightest">volume_up</i>
      <div class="w-20 ml-1 bg-lightest rounded-full h-1"></div>
    </div>
  </div>
</template>

<script>
import song from "../assets/aShortStory.mp3";

export default {
  data() {
    return {
      pause: false,
    };
  },
  methods: {
    playSong() {
      if (!this.pause) {
        let audio = new Audio(song);
        audio.play();
        this.pause = this.pause === true ? false : true;
      }
    },
  },
};
</script>

<style></style>
