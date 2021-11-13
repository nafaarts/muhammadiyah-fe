<template>
  <div
    class="h-screen w-60 shadow-md absolute top-0 left-0 bg-white p-5 sidebar"
    :class="{ active: showSideBar }"
  >
    <nuxt-link to="/">
      <img src="~assets/logo.png" alt="logo" width="150" class="m-auto">
    </nuxt-link>
    <hr class="my-5">
    <ul class="menu">
      <li class="submenu">
        <nuxt-link class="mr-5 hover:text-gray-900" to="/">
          Beranda
        </nuxt-link>
      </li>
      <li class="submenu">
        <nuxt-link class="mr-5 hover:text-gray-900" to="/informasi">
          Informasi
        </nuxt-link>
      </li>
      <li class="submenu">
        <nuxt-link class="mr-5 hover:text-gray-900" to="/galeri">
          Galeri
        </nuxt-link>
      </li>
      <li class="submenu">
        <nuxt-link class="mr-5 hover:text-gray-900" to="/galeri">
          Tentang
        </nuxt-link>
      </li>
    </ul>
    <hr class="my-5">

    <nuxt-link
      to="/donasi"
      class="
        inline-flex
        items-center
        bg-green-700
        border-0
        py-1
        px-3
        focus:outline-none
        hover:bg-green-500
        rounded
        text-white
        ml-5
        flex
      "
    >
      Ayo Donasi
      <svg
        fill="none"
        stroke="currentColor"
        stroke-linecap="round"
        stroke-linejoin="round"
        stroke-width="2"
        class="w-4 h-4 ml-1"
        viewBox="0 0 24 24"
      >
        <path d="M5 12h14M12 5l7 7-7 7" />
      </svg>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    showSideBar: Boolean
  }
}
</script>

<style scoped>
.sidebar {
  transform: translateX(-250px);
  transition: 0.3s;
}

.sidebar.active {
  transform: translateY(0);
}

.menu {
  font-size: 18px;
  margin-left: 20px;
}

.menu .submenu {
  margin-bottom: 20px;
}
</style>
