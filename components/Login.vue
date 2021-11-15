<template>
  <div class="grid grid-cols-8 gap-4 bg-gray-200 w-screen h-screen">
    <div class="col-start-4 col-end-6 bg-white mt-20 mb-20 rounded-md">
      <div class="flex justify-center text-3xl font-bold mt-10 text-purple-800">
        <img src="../assets/LOGO1.png"  alt="">
      </div>
      <div class="mx-10 mt-10">
        <p class="text-lg font-bold text-purple-600">Email</p>
        <input type="email" class="px-2 py-1 mt-3 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none">
        <p class="text-lg font-bold text-purple-600 mt-5">Password</p>
        <input type="password" class="px-2 py-1 mt-3 w-full bg-gray-200 border-2 border-gray-300 focus:outline-none">
        <div class="flex justify-center mt-10">
          <button type="button" class="bg-purple-600 text-2xl text-white rounded-md px-5 py-2 focus:outline-none" @click="login">Login</button>
        </div>
        <div class="flex justify-center mt-5">
          <p>Not Register yet? <a href="/signup" class="text-purple-600 underline">SignUp</a></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  methods: {
    login() {
      document.location = '/listings';
    }
  }
}
</script>

<style>

</style>
