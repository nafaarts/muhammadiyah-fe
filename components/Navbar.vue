<template>
  <!-- header -->
  <header
    class="text-gray-600 bg-white body-font fixed w-full top-0 z-50"
    :class="{ 'shadow-md': isScroll }"
  >
    <div class="lg:mx-8 sm:mx-2">
      <div
        class="
          container
          mx-auto
          flex
          md:p-5
          p-3
          justify-between
          md:flex-row
          items-center
        "
      >
        <nuxt-link
          to="/"
          class="flex title-font font-medium items-center text-gray-900 mb-0"
        >
          <img src="~assets/logo.png" alt="logo" width="150">
        </nuxt-link>
        <nav
          class="
            md:block
            hidden
            md:ml-auto md:mr-auto
            flex flex-wrap
            items-center
            text-base
            justify-center
          "
        >
          <nuxt-link class="mr-5 hover:text-gray-900" to="/">
            Beranda
          </nuxt-link>
          <nuxt-link class="mr-5 hover:text-gray-900" to="/informasi">
            Informasi
          </nuxt-link>
          <nuxt-link class="mr-5 hover:text-gray-900" to="/galeri">
            Galeri
          </nuxt-link>
          <nuxt-link class="mr-5 hover:text-gray-900" to="/galeri">
            Tentang
          </nuxt-link>
        </nav>
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
            mt-4
            md:mt-0
            hidden
            md:flex
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
        <button class="inline md:hidden mr-2">
          <svg width="24" height="24" viewBox="0 0 24 24">
            <path d="M24 6h-24v-4h24v4zm0 4h-24v4h24v-4zm0 8h-24v4h24v-4z" />
          </svg>
        </button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data () {
    return {
      isScroll: false
    }
  },
  mounted () {
    // window.addEventListener('scroll', this.addShadow)
    window.addEventListener('scroll', () => {
      if (window.scrollY > 20) {
        this.isScroll = true
      } else {
        this.isScroll = false
      }
    })
  }
}
</script>
