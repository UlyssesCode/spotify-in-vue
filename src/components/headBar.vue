<template>
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
        @click="show = true"
        class="bg-light rounded-full p-1 px-2 flex items-center"
      >
        <img
          class="rounded-full h-6 w-6"
          src="../assets/avater.jpg"
          alt="avater"
        />
        <p class="text-white font-semibold text-xs mr-1">十月之水</p>
        <i v-if="show === false" class="material-icons text-white">
          arrow_drop_down
        </i>
        <i v-if="show === true" class="material-icons text-white">
          arrow_drop_up
        </i>
      </button>
      <div v-if="show === true" class="absolute bg-light w-full rounded mt-1">
        <button
          @click="show = false"
          class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
        >
          账户
        </button>
        <button
          @click="show = false"
          class="w-full text-sm py-2 text-lightest hover:text-white opacity-75 hover:opacity-100"
        >
          退出
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: this.showDropdown,
    };
  },
  props: ["showDropdown"],
};
</script>

<style></style>
