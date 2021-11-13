<template>
  <main>
    <Navbar />
    <Hero />
    <About />
    <News :limit="true" />
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
