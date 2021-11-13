<template>
  <main>
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
