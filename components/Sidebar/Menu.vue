<template>
  <div>
    <header class="flex items-center gap-2 p-4">
      <div class="">
        <NuxtLink
          class="flex items-center gap-2 hover:scale-[101%] transition cursor-pointer"
          to="/"
        >
          <Logo />
          <p class="font-bold text-black">Nuxt-Finance</p></NuxtLink
        >
      </div>
    </header>
    <div class="px-4 grow">
      <div class="grid gap-2">
        <div
          class="flex items-center gap-2 px-2 py-1 transition rounded cursor-pointer hover:bg-neutral-100"
          v-for="(item, index) in items"
          :key="index"
        >
          <Icon :name="item.icon" />
          <NuxtLink :to="item.link" class="text-neutral-900">{{
            item.title
          }}</NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const items = ref([
  { title: "Overview", icon: "ri:dashboard-line", link: "/" },
  {
    title: "Transactions",
    icon: "grommet-icons:transaction",
    link: "/transactions",
  },
  { title: "Account", icon: "mingcute:settings-1-line", link: "/user" },
  {
    title: "Contacts",
    icon: "ic:outline-perm-contact-calendar",
    link: "/contacts",
  },
  {
    title: "Settings",
    icon: "material-symbols:settings-outline",
    link: "/settings",
  },
]);
</script>

<style></style>
