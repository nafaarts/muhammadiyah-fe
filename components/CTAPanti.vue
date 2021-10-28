<template>
  <section class="bg-green-800 text-white py-20 cta-panti-background bg-fixed">
    <div class="mx-8 text-center block">
      <h1 class="text-3xl mb-2 font-medium">
        PANTI ASUHAN
      </h1>
      <h1 class="text-2xl mb-4">
        YAYASAN KESEJAHTERAAN SOSIAL MUHAMMADIYAH
      </h1>
      <p class="mb-4 text-base">
        "Sebesar apa pun kebaikan itu, walau hanya sebesar biji zarah akan
        dibalas oleh allah SWT."
        <br>(QS. At Taubah: 105)
      </p>
      <hr class="w-24 my-10 m-auto">
      <nuxt-link
        to="/donasi"
        class="border-2 py-2 px-4 rounded hover:bg-white hover:text-black"
      >
        Donasi Yuk
      </nuxt-link>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style>
.cta-panti-background {
  background-image: url(~assets/cta-panti.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}
</style>
