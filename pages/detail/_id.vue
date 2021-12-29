<template>
  <ListingDetails :id="id" />
</template>

<script>
import ListingDetails from '../../components/ListingDetails'

export default {
  components: {
    ListingDetails: ListingDetails
  },
  async asyncData({ params }) {
    const id = params.id
    return { id }
  }
}
</script>

<style>

</style>
