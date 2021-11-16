<template>
  <main>
    <Navbar />
    <div class="min-h-screen">
      <News :limit="false" />
    </div>
    <WhatsApp />
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
