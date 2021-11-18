<template>
  <div class="grid grid-cols-4 bg-gray-200 w-screen h-full relative">
    <Leftside />
    <div class="col-start-2 col-end-5 border-2 border-gray-200">
      <Topside />
      <div class="flex justify-between">
        <div>
          <p class="font-bold mt-3 mx-5 text-3xl">Rewards</p>
        </div>
        <input type="text" class="bg-white h-8 px-3 py-2 mr-10 mt-3 placeholder-opacity" placeholder="Wallet Address">
      </div>
      <div class="bg-white ml-3 mr-10 mt-1 rounded-md">
        <div class="flex justify-center">
          <div class="mt-10 mx-10 bg-gray-200 border-dashed border-2 border-gray-300 rounded">
            <div class="flex justify-center">
              <div class="font-bold text-xl -mt-5 mx-10 bg-gray-200 border-dashed border-2 border-gray-300 rounded text-center w-40">
                Your Wallet
              </div>
            </div>
            <div class="flex gap-5 justify-center mt-10 mb-10">
              <div class="bg-purple-700 text-white py-6 px-4 ml-10 rounded">
                <div class="bg-white -mt-10 float-right">
                  <img src="../assets/photo.jpg" class="rounded-full" alt="">
                </div>
                <p>100,234,344,100</p>
              </div>
              <div class="bg-yellow-600 text-gray-700 py-6 px-2 mr-10 rounded">
                <div class="bg-white -mt-10 float-right">
                  <img src="../assets/busd.png" class="rounded-full" alt="">
                </div>
                <p class="mx-10">$499.73</p>
              </div>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="mt-10 mx-10 mb-10 bg-gray-200 border-dashed border-2 border-gray-300 rounded">
            <div class="flex justify-center">
              <div class="font-bold text-xl -mt-5 mx-10 bg-gray-200 border-dashed border-2 border-gray-300 rounded text-center w-40">
                BUSD Rewards
              </div>
            </div>
            <div class="flex gap-5 justify-center mt-10 mb-10">
              <div>
                <p class="ml-10 -mt-10 mb-3 font-bold text-lg">Pending</p>
                <div class="bg-green-300 text-green-700 py-6 px-10 ml-10 rounded">
                  <div class="bg-white -mt-10 float-right -mr-6">
                    <img src="../assets/busd.png" class="rounded-full" alt="">
                  </div>
                  <p class="mx-4">$1.63</p>
                </div>
              </div>
              <div>
                <p class="-mt-10 mb-3 font-bold text-lg">Total</p>
                <div class="bg-pink-200 text-pink-700 py-6 px-2 mr-10 rounded">
                  <div class="bg-white -mt-10 float-right">
                    <img src="../assets/busd.png" class="rounded-full" alt="">
                  </div>
                  <p class="mx-10">$200.66</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="grid grid-cols-2 gap-4 ml-3 mr-10 mt-5 mb-10">
        <div class="col-start-1 col-end-2 bg-white rounded">
          <div class="mt-5 ml-10">
            <p class="text-xl text-gray-600 font-semibold">Reward Distributed To Holders</p>
            <div class="flex mb-5 gap-3 mt-5">
              <p class="text-xl text-yellow-500 font-semibold">$19521668.638</p>
              <SvgIcon text="distribute" />
            </div>
          </div>
        </div>
        <div class="col-start-2 col-end-3 bg-white rounded">
          <div class="flex mt-5 ml-10">
            <img src="../assets/photo1.jpg" class="rounded-full" alt="">
            <p class="text-xl font-semibold ml-5">Shiba Contract</p>
          </div>
          <div class="flex ml-10">
            <p class="text-gray-500">0x52941a733F7bAb6E52d5c8f2045c9D9D9eA246Ff</p>
            <SvgIcon text="Shibawatch" />
          </div>
          <div class="flex mt-5 ml-10">
            <SvgIcon text="distribute" />

            <p class="text-xl font-semibold ml-5">BUSD Contract</p>
          </div>
          <div class="flex ml-10 mb-2">
            <p class="text-gray-500">0x52941a733F7bAb6E52d5c8f2045c9D9D9eA246Ff</p>
            <SvgIcon text="busd_copy" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'
import SvgIcon from './SvgIcon';
import Leftside from './Leftside'
import Topside from './Topside'

export default {
  components: {
    Multiselect,
    SvgIcon,
    Leftside,
    Topside
},
  data() {
    return {
      value: [],
      options: ['Listings', 'Audit', 'KYC', 'ShibaWatch Swap'],
      }
  },
  methods: {
    signin() {
      document.location = '/login';
    },
    select() {
      var acc = document.getElementsByClassName("accordion");
      var i;

      for (i = 0; i < acc.length; i++) {
        acc[i].addEventListener("click", function() {
          this.classList.toggle("active");
          var panel = this.nextElementSibling;
          if (panel.style.display === "block") {
            panel.style.display = "none";
          } else {
            panel.style.display = "block";
          }
        });
      }
    },
    createlist() {

    }
  }
}

</script>

<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>
<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
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
