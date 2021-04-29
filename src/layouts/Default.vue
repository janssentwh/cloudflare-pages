<template>
  <div class="container-fluid">
    <notifications />
    <Navbar />
    <section class="section">
      <slot />
    </section>
    <LegalAge />
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'
import LegalAge from '@/components/LegalAge'

export default {
  components: { Navbar, LegalAge }
}
</script>
