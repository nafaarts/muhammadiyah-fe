<template>
  <main>
    <Navbar :hide-sized-box="true" />
    <Hero />
    <About />
    <News :limit="true" class="py-10" />
    <CTAPanti />
    <Staff />
    <Maps />
    <Footer />
  </main>
</template>

<script>
export default {
  head () {
    return {
      title: 'Beranda - Muhammadiyah Banda Aceh'
    }
  }
}
</script>
