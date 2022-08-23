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
            class="transition duration-400 flex items-center justify-start opacity-75 hover:opacity-100 mb-2"
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
            class="transition duration-400 flex items-center justify-start opacity-75 hover:opacity-100"
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
          <img src="./assets/BETTER LATE THAN NEVER .jpg" alt="album-cover" />
        </div>
      </div>
      <!-- main content -->
      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <div
          class="v-full sticky top-0 py-4 px-6 flex items-center justify-between bg-black"
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
                退出
              </button>
            </div>
          </div>
        </div>
        <!-- cards -->
        <div>
          <div class="px-6 py-3 flex justify-between items-center">
            <h1
              class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline"
            >
              最近播放
            </h1>
            <h2
              class="pr-8 pt-4 text-xs text-lightest tracking-wider hover:underline mb-3"
            >
              查看全部
            </h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div
              v-for="recent in recents"
              :key="recent.src"
              class="p-2 w-48 pl-7 relative"
            >
              <div
                class="absolute w-full h-full flex items-end justify-end p-10 pb-6 opacity-0 hover:opacity-100 hover:pb-8 transition-all duration-300"
              >
                <div
                  class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
                >
                  <i class="material-icons text-4xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img
                  :src="`${recent.src}`"
                  :alt="`${recent.title}-cover`"
                  class="h-auto w-full shadow mb-2"
                />
                <h1
                  class="w-full inline-block whitespace-nowrap truncate ... text-sm font-semibold text-white tracking-wide"
                  :title="recent.title"
                >
                  {{ recent.title }}
                </h1>
                <h2
                  class="pb-4 text-xs text-lightest tracking-wide"
                  :title="recent.artist"
                >
                  {{ recent.artist }}
                </h2>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="px-6 py-3 flex justify-between items-center">
            <h1
              class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline"
            >
              根据十月之水的喜好推荐
            </h1>
            <h2
              class="pr-8 pt-4 text-xs text-lightest tracking-wider hover:underline mb-3"
            >
              查看全部
            </h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div
              v-for="fory in forys"
              :key="fory.src"
              class="p-2 w-48 pl-7 relative"
            >
              <div
                class="absolute w-full h-full flex items-end justify-end p-10 pb-6 opacity-0 hover:opacity-100 hover:pb-8 transition-all duration-300"
              >
                <div
                  class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
                >
                  <i class="material-icons text-4xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img
                  :src="`${fory.src}`"
                  :alt="`${fory.title}-cover`"
                  class="h-auto w-full shadow mb-2"
                />
                <h1
                  class="w-full inline-block whitespace-nowrap truncate ... text-sm font-semibold text-white tracking-wide"
                  :title="fory.title"
                >
                  {{ fory.title }}
                </h1>
                <h2
                  class="w-full line-clamp-1 pb-4 text-xs text-lightest tracking-wide"
                  :title="fory.artist"
                >
                  {{ fory.artist }}
                </h2>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="px-6 py-3 flex justify-between items-center">
            <h1
              class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline"
            >
              回味无穷
            </h1>
            <h2
              class="pr-8 pt-4 text-xs text-lightest tracking-wider hover:underline mb-3"
            >
              查看全部
            </h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div
              v-for="cus in cuss"
              :key="cus.src"
              class="p-2 w-48 pl-7 relative"
            >
              <div
                class="absolute w-full h-full flex items-end justify-end p-10 pb-6 opacity-0 hover:opacity-100 hover:pb-8 transition-all duration-300"
              >
                <div
                  class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
                >
                  <i class="material-icons text-4xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img
                  :src="`${cus.src}`"
                  :alt="`${cus.title}-cover`"
                  class="h-auto w-full shadow mb-2"
                />
                <h1
                  class="w-full inline-block whitespace-nowrap truncate ... text-sm font-semibold text-white tracking-wide"
                  :title="cus.title"
                >
                  {{ cus.title }}
                </h1>
                <h2
                  class="w-full line-clamp-1 pb-4 text-xs text-lightest tracking-wide"
                  :title="cus.artist"
                >
                  {{ cus.artist }}
                </h2>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- play bar -->
    <div
      class="w-full flex items-center justify-between px-3 bg-light"
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
      <div class="flex flex-col justify-center w-1/3 items-center">
        <div class="flex items-center">
          <button class="mx-5 text-lightest hover:text-white">
            <i class="material-icons text-lg">shuffle</i>
          </button>
          <button class="text-lightest hover:text-white">
            <i class="material-icons text-lg">skip_previous</i>
          </button>
          <button
            class="rounded-full h-10 w-10 flex items-center mx-5 justify-center text-white hover:text-white"
          >
            <i class="material-icons text-2xl">play_circle</i>
          </button>
          <button class="text-lightest hover:text-white">
            <i class="material-icons text-lg">skip_next</i>
          </button>
          <button class="mx-5 text-lightest hover:text-white">
            <i class="material-icons text-lg">repeat</i>
          </button>
        </div>
        <div class="w-full">
          <div class="w-full h-1 bg-lightest rounded-full mt-4"></div>
        </div>
      </div>
      <div class="flex items-center">
        <i class="mx-2 material-icons text-xl text-lightest">playlist_play</i>
        <i class="mx-2 material-icons text-xl text-lightest">cast</i>
        <i class="mx-2 material-icons text-xl text-lightest">volume_up</i>
        <div class="w-20 ml-1 bg-lightest rounded-full h-1"></div>
      </div>
    </div>
  </div>
</template>

<script>
import rec0 from "./assets/rec0.jpg";
import rec1 from "./assets/rec1.jpg";
import rec2 from "./assets/rec2.jpg";
import rec3 from "./assets/rec4.jpg";
import rec4 from "./assets/rec5.jpg";
import rec5 from "./assets/rec3.jpg";

import for0 from "./assets/for0.jpg";
import for1 from "./assets/for1.jpg";
import for2 from "./assets/for2.jpg";
import for3 from "./assets/for3.jpg";
import for4 from "./assets/for4.jpg";
import for5 from "./assets/for5.jpg";

import cus0 from "./assets/cus0.jpg";
import cus1 from "./assets/cus1.jpg";
import cus2 from "./assets/cus2.jpg";
import cus3 from "./assets/cus3.jpg";
import cus4 from "./assets/cus4.jpg";
import cus5 from "./assets/cus5.jpg";

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
      albums: [{ name: "我的歌单#1" }, { name: "生命之光" }],
      showDropdown: false,
      recents: [
        { src: rec0, title: "Daily Mix", artist: "By Spotify" },
        { src: rec1, title: "孤独的人是可耻的", artist: "张楚" },
        { src: rec2, title: "一无所有", artist: "崔健" },

        { src: rec3, title: "只爱陌生人", artist: "王菲" },
        {
          src: rec4,
          title: "The Dark Side of the Moon",
          artist: "Pink Floyd",
        },
        {
          src: rec5,
          title: "In The Court Of The Crimson King",
          artist: "King Crimson",
        },
      ],
      forys: [
        {
          src: for0,
          title: "今日推荐2",
          artist: "腰樂隊、五條人、JADE EYES 等更多曲风",
        },
        {
          src: for1,
          title: "新歌雷达",
          artist:
            "捕捉你关注的艺人的最新音乐，以及为你推荐的最新单曲。每周五更新。",
        },
        {
          src: for2,
          title: "每周新发现",
          artist:
            "你的每周新鲜音乐合辑。畅享符合你喜好的新音乐和精选辑。每周一更新。",
        },

        {
          src: for3,
          title: "今日推荐4",
          artist: "Eason Chan、Faye Wong、Wakin Chau 等更多曲风",
        },
        {
          src: for4,
          title: "今日推荐5",
          artist: "The Beatles、Camel、Pink Floyd 等更多曲风",
        },
        {
          src: for5,
          title: "今日推荐3",
          artist: "Frank Zappa、King Crimson、Caravan 等更多曲风",
        },
      ],
      cuss: [
        {
          src: cus0,
          title: "罗大佑 合辑",
          artist: "窦唯、万能青年旅店、小虎队 等更多曲风",
        },
        {
          src: cus1,
          title: "当时的月亮 电台",
          artist: "创建者：Spotify",
        },
        {
          src: cus2,
          title: "寸铁 电台",
          artist: "创建者：Spotify",
        },

        {
          src: cus3,
          title: "野外合作社 合辑",
          artist: "甜梅号、张楚、Joyside等更多曲风",
        },
        {
          src: cus4,
          title: "陈升 合辑",
          artist: "声音碎片、腰乐队、伍佰 等更多曲风",
        },
        {
          src: cus5,
          title: "最爱MyLittleAirport",
          artist:
            "My Little Airport 嘅歌一直帶大家遊走香港，每張專輯盛載住呢個城市嘅變遷...",
        },
      ],
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
