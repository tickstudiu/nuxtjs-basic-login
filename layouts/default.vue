<template>
  <div>
    <Navbar/>
    <b-container class="my-3">
      <Nuxt />
    </b-container>
  </div>
</template>

<script>
import Navbar from '@/components/navbar';

export default {
  component: {
    Navbar,
  }
}
</script>

