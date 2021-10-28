<template>
  <main class="md:pt-6 pt-24">
    <Navbar />
    <News :limit="false" />
    <Footer />
  </main>
</template>

<script>
export default {
  head () {
    return {
      title: 'Informasi - Muhammadiyah Banda Aceh'
    }
  }
}
</script>
