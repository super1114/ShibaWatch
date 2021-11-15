<template>
  <div>
    <CoinListing />
    <Listings />
  </div>
</template>

<script>
import Listings from '../components/Listings'
import CoinListing from '~/components/CoinListing.vue'

export default {
  components: {
    Listings: Listings,
    CoinListing: CoinListing
}
}
</script>

<style>

</style>
