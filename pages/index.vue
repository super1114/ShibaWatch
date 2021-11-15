<template>
  <div>
    <CoinListing />
  </div>
</template>

<script>
import CoinListing from '@/components/CoinListing'

export default {
  name: 'LandingPage',
  components: {
    CoinListing: CoinListing
  }
}
</script>
