<template>
  <div class="grid grid-cols-8 gap-4 bg-gray-200 w-screen h-screen">
    <div class="col-start-4 col-end-6 bg-white mt-20 mb-20">
      <div class="flex justify-left text-3xl font-bold text-purple-800 mt-2 mx-2">
        <img src="../assets/LOGO2.png" alt="">
      </div>
      <div class="mx-10 mt-10">
        <p class="text-lg font-bold text-purple-600">UserName</p>
        <input type="text" class="px-2 py-1 placeholder-opacity-100 mt-3 py-2 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none" placeholder="Shiba Watch">
        <p class="text-lg font-bold text-purple-600 mt-5">Email</p>
        <input type="email" class="px-2 py-1 placeholder-opacity-100 mt-3 py-2 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none" placeholder="ShibaWatch@shibawatch.com">
        <p class="text-lg font-bold text-purple-600 mt-5">Password</p>
        <input type="password" class="px-2 py-1 mt-3 py-2 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none">
        <p class="text-lg font-bold text-purple-600 mt-5">Confirm</p>
        <input type="password" class="px-2 py-1 mt-3 py-2 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none">
        <div class="flex justify-center mt-5 mb-5">
          <button type="button" class="bg-purple-600 text-2xl text-white rounded-md px-5 py-2 focus:outline-none" @click="signup">Signup</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  methods: {
    signup() {
      document.location = '/login';
    }
  }
}
</script>

<style>

</style>
