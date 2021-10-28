<template>
  <section
    class="text-gray-700 body-fon hero-background md:py-0 py-10 lg:h-screen"
  >
    <div class="lg:mx-8 sm:mx-2">
      <div
        class="
          container
          mx-auto
          flex
          px-5
          md:py-24
          sm:py-14
          md:flex-row
          flex-col
          items-center items-center
          lg:h-screen
        "
      >
        <div
          class="
            lg:flex-grow
            md:w-1/2
            lg:pr-24
            md:pr-16
            flex flex-col
            md:items-start md:text-left
            mb-2
            md:mb-0
            items-center
            text-center
            lg:ml-14
            sm:ml-0
          "
        >
          <h4 class="lg:text-5xl">
            PIMPINAN DAERAH
          </h4>
          <h1 class="title-font lg:text-6xl font-medium focus-muhammadiyah">
            MUHAMMADIYAH
          </h1>
          <h4 class="sm:text-5xl mb-4">
            KOTA BANDA ACEH
          </h4>
          <hr class="border border-2 bg-black w-40 mb-4">
          <small
            class="leading-relaxed"
          >Dikelola oleh Sekretariat Pimpinan Daerah</small>
        </div>
        <div class="lg:max-w-lg lg:w-full md:w-1/2 w-5/6">
          <img
            class="object-cover object-center rounded"
            alt="hero"
            src="~assets/illustrasi-pas.png"
          >
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style>
.focus-muhammadiyah {
  background: -webkit-linear-gradient(#058d4e, #ffd600);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-background {
  background-image: url(~assets/bg-hero.png);
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center bottom;
}
</style>
