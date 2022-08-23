<template>
  <div>
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
        <div v-for="cus in cuss" :key="cus.src" class="p-2 w-48 pl-7 relative">
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
</template>

<script>
export default {
  props: ["recents", "forys", "cuss"],
};
</script>

<style></style>
