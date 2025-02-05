<template>
  <div class="px-4 py-2">
    <div class="navbar bg-base-200 p-0">
      <div class="flex-1 gap-2">
        <img
          alt="Tailwind CSS Navbar component"
          src="https://d1hv7ee95zft1i.cloudfront.net/custom/car-model-color-photo/small/toyota-avanza-black-metallic-65c346ee9bd4d.webp"
          class="w-14 rounded-lg border-2 border-gray-300"
        />
        <div>
          <p class="text-xl">Asep Gunawan</p>
          <p class="text-gray-600 text-[14px]">081383610802</p>
        </div>
      </div>
      <div class="flex-none gap-2">
        <button class="btn btn-sm w-10 h-10 border-2 bg-white border-gray-300">
          <Icon
            name="fa6-solid:ellipsis-vertical"
            size="18px"
            class="bg-gray-600"
          />
        </button>
        <button
          class="btn btn-sm h-10 border-2 bg-blue-500 text-white border-blue-500"
        >
          Edit Driver
        </button>
      </div>
    </div>
    <div class="border-b-4 mt-2">
      <nav class="flex text-gray-500 text-sm">
        <a
          href="/"
          class="p-2 px-6 flex items-center gap-2"
          :class="{
            'text-blue-500 border-blue-500 border-b-4 relative top-1':
              route.path === '/',
          }"
          ><Icon name="fa6-regular:user" /> OVERVIEW</a
        >
        <a
          href="/live-tracking"
          class="p-2 px-6 flex items-center gap-22"
          :class="{
            'text-blue-500 border-blue-500 border-b-4 relative top-1':
              route.path === '/live-tracking',
          }"
          ><Icon name="ic:round-lock-open" /> LIVE TRACKING</a
        >
        <a
          href="/driver-behavior"
          class="p-2 px-6 flex items-center gap-2"
          :class="{
            'text-blue-500 border-blue-500 border-b-4 relative top-1':
              route.path === '/driver-behavior',
          }"
          ><Icon name="fa6-regular:bookmark" /> DRIVER BEHAVIOR</a
        >
        <a
          href="/notification"
          class="p-2 px-6 flex items-center gap-2"
          :class="{
            'text-blue-500 border-blue-500 border-b-4 relative top-1':
              route.path === '/notification',
          }"
          ><Icon name="fa6-regular:bell" /> NOTIFICATION</a
        >
      </nav>
    </div>
    <slot />
  </div>
</template>
<script setup lang="ts">
import { useRoute } from "vue-router";

const route = useRoute();
</script>
