<template>
  <div>
    <div
      class="flex md:hidden z-50 items-center justify-between w-full h-full p-4"
    >
      <Logo />
      <Icon
        class="z-50 cursor-pointer"
        name="iconamoon:menu-burger-horizontal"
        size="30"
        @click="open = !open"
      />
      <transition name="sidebar">
        <div
          v-if="open"
          class="fixed bg-green-100 shadow-xl top-0 left-0 z-[999] w-full h-screen"
        >
          <Icon
            class="absolute z-50 cursor-pointer right-4 top-4"
            name="material-symbols:close"
            size="30"
            @click="open = !open"
          />
          <SidebarMenu />
        </div>
      </transition>
    </div>
    <div
      class="hidden md:flex w-[250px] h-screen flex-col justify-between border-r-emerald-300 border-r"
    >
      <SidebarMenu />
      <div>UserItem</div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const open = ref(false);
</script>

<style>
@keyframes widen {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

.sidebar-enter-active {
  animation: widen 0.3s;
}
.sidebar-leave-active {
  animation: widen 0.3s reverse;
}
</style>
