<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <!-- side nav -->

      <SideNav :pages="pages" :setID="setID" :albums="albums" />
      <!-- main content -->
      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <HeadBar :show="showDropdown" />
        <!-- cards -->
        <MainCards :recents="recents" :forys="forys" :cuss="cuss" />
      </div>
    </div>
    <!-- play bar -->
    <PlayBar />
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

import SideNav from "./components/sideNav.vue";
import HeadBar from "./components/headBar.vue";
import MainCards from "./components/mainCards.vue";
import PlayBar from "./components/playBar.vue";

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
  components: { SideNav, HeadBar, MainCards, PlayBar },
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
