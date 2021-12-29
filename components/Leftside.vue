<template>
  <div class="relative">
    <div :class="this.is_mobile?'hide_sidebar':''" class="col-span-1 bg-white mt-20 mb-10 px-5 rounded-tr-lg rounded-br-lg shadow-md sticky h-full">
      <a href="/"><img  src="../assets/LOGO1.png" class="-mt-12" alt=""></a>

      <div class="mt-20 font-bold text-gray-700 text-center py-4 hover:bg-gray-200"><a href="/">Listing</a></div>
      <div class="mt-5 font-bold text-gray-700 text-center py-4 hover:bg-gray-200"><a href="/rewards">Rewards</a></div>
    </div>
    <div :class="this.is_mobile?'':'hide_sidebar'" class="flex items-center justify-between px-5 py-2 bg-white border-2 border-gray-200 col-span-4">
        <a href="/"><img src="../assets/LOGO1.png" class="w-40" /></a>
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 cursor-pointer" fill="none" viewBox="0 0 24 24" stroke="currentColor" @click="mobileMenu">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
    </div>
    <div :class="is_mobile&&mobile_menu?'':'hidden'" class="absolute right-0 top-0 w-3/4 z-50 h-screen bg-gray-100 border-gray-400 border-2 rounded-md">
      <div class="">
        <div class="float-right px-3 py-3">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" @click="mobileMenu">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </div>
        <div class="block pt-20">
          <ul>
            <li ><a href="/" class="block px-2 py-4 hover:bg-green-500 transition duration-300 text-md text-center">Listing</a></li>
            <li ><a href="/rewards" class="block px-2 py-4 hover:bg-green-500 transition duration-300 text-md text-center">Rewards</a></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        is_mobile:false,
        mobile_menu:false
      }
    },
    mounted() {
      if(window.innerWidth<1024) {
        this.is_mobile = true;
      }
    },
    methods: {
      mobileMenu() {
        this.mobile_menu = !this.mobile_menu;
      },
      select(num) {
        if(num==1&&this.is_mobile) {this.$refs.drop3.nextElementSibling.style.display= this.$refs.drop3.nextElementSibling.style.display=="block"? "none": "block";}
        if(num==1&&!this.is_mobile) {this.$refs.drop1.nextElementSibling.style.display= this.$refs.drop1.nextElementSibling.style.display=="block"? "none": "block";}
        if(num==2&&this.is_mobile) {this.$refs.drop4.nextElementSibling.style.display= this.$refs.drop4.nextElementSibling.style.display=="block"? "none": "block";}
        else {this.$refs.drop2.nextElementSibling.style.display= this.$refs.drop2.nextElementSibling.style.display=="block"? "none": "block";}
      }
    }
  }
</script>
<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.hide_sidebar {
  display: none;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
button[disabled="disabled"]{
  cursor: not-allowed;
  opacity: 0.8;
}
button.vsa-item__trigger {
  width: 100%;
}
div.leftbox {
  box-shadow:
  0 2.8px 2.2px rgba(0, 0, 0, 0.034),
  0 6.7px 5.3px rgba(0, 0, 0, 0.048),
  0 12.5px 10px rgba(0, 0, 0, 0.06);
}

.accordion {
  background-color: #eee;
  color: #444;
  cursor: pointer;
  padding: 5px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  font-size: 20px;
  font: bold;
  transition: 0.4s;
}
.active, .accordion:hover {
  background-color: #ccc;
  color: blue;
  outline: none;
}

.panel {
  color:#a0aec0;
  padding: 0 18px;
  display: none;
  background-color: white;
  overflow: hidden;
}


</style>
