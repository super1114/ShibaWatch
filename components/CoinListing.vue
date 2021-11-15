<template>
  <div class="grid grid-cols-4 bg-gray-200 w-screen h-screen relative">
    <div class="col-start-1 col-end-2 bg-white mt-20 mb-10 px-5 rounded-tr-lg rounded-br-lg shadow-md sticky">
      <img class="absolute -mt-12" src="../assets/LOGO1.png" alt="">
      <div class="mt-20">
        <button class="accordion" @click="select">
          <div class="flex justify-between">
            <p>TokenRelated</p>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
            </svg>
        </div>
        </button>
        <div class="panel">
          <div class="mt-3 hover:text-blue-600"><a href="/">Listings</a></div>
          <div class="mt-3 hover:text-blue-600"><a href="#">Audit</a></div>
          <div class="mt-3 hover:text-blue-600"><a href="#">KYC</a></div>
          <div class="mt-3 hover:text-blue-600"><a href="/listingdetails">ShibaWatch SWAP</a></div>
        </div>
      </div>
      <div class="mt-5 text-gray-500 font-semibold text-sm">
        OTHER FUNCTIONS
      </div>
      <div class="mt-5">
        <button class="accordion" @click="select">
          <div class="flex justify-between">
            <p>Stake and Lend</p>
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 mt-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
            </svg>
          </div>
        </button>
        <div class="panel">
          <div class="mt-3 hover:text-blue-600"><a href="#">Stake</a></div>
          <div class="mt-3 hover:text-blue-600"><a href="#">Audit</a></div>
        </div>
      </div>
      <div class="mt-5 font-bold text-gray-700">NFT Marketplace</div>
      <div class="mt-5 font-bold text-gray-700"><a href="/rewards">Rewards</a></div>
    </div>
    <div class="col-start-2 col-end-5 border-2 border-gray-200">
      <div class="w-full bg-white -mx-2 flex justify-between border-2 border-gray-300">
        <div></div>
        <div class="flex">
          <button type="button" class="bg-purple-800 mx-1 px-5 py-2 mt-6 mb-6 text-white rounded-lg cursor-pointer focus:outline-none" @click="signin">Sign In</button>
          <div class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">Connect Wallet</div>
        </div>
      </div>
      <div class="flex justify-between">
        <div>
          <p class="font-bold mt-3 mx-5 text-3xl">Listings</p>
          <p class="mx-5 mt-2 font-semibold text-gray-700">We collate and streamline all existing and upcoming coins all in one  listing</p>
        </div>
        <div class="flex mt-10 h-10 bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mt-1 mx-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
          </svg>
          <a href="/create"><p>Create Listing</p></a>
        </div>
      </div>
      <div class="bg-white ml-3 mr-10 mt-1 rounded-md">
        <div class="flex">
          <div class="flex mt-3 ml-5">
            <div class="flex border-2 rounded h-8">
                <button class="flex items-center justify-center px-4 bg-white">
                    <svg class="w-5 h-5 text-green-300" fill="currentColor" xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 24 24">
                        <path
                            d="M16.32 14.9l5.39 5.4a1 1 0 0 1-1.42 1.4l-5.38-5.38a8 8 0 1 1 1.41-1.41zM10 16a6 6 0 1 0 0-12 6 6 0 0 0 0 12z">
                        </path>
                    </svg>
                </button>
                <input type="text" class="px-4 py-2 w-80 focus:outline-none" placeholder="Search...">
            </div>
          </div>
          <div class="flex justify-between">
            <div class="flex">
              <div class="w-3 h-3 rounded-full bg-green-500 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">Audited</p>
              <div class="w-3 h-3 rounded-full bg-purple-700 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">KYC</p>
              <div class="w-3 h-3 rounded-full bg-pink-500 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">Doxxed</p>
            </div>
            <p class="mt-5 mx-20 text-xs"><span class="text-gray-500">Sortby:</span>Name</p>
            <p class="mt-5 mx-5 text-xs text-gray-500">Rows per page:5</p>
            <p class="mt-5 mx-5 text-xs text-gray-500">1-5 of 5</p>
            <p class="mt-5 mx-5 text-xs cursor-pointer">< ></p>
          </div>
        </div>
        <table class="table-auto mt-5 w-full p-10">
            <thead class="border-b-2 bg-gray-200 border-gray-300 border-t-2 border-gray-300">
              <tr class="">
                <th class="invisible bg-gray-300">avatar</th>
                <th class="text-left text-gray-800 font-semibold text-sm">NAME</th>
                <th class="text-left text-gray-800 font-semibold text-sm">METRICS</th>
                <th class="text-left text-gray-800 font-semibold text-sm">SOCIAL MEDIA STRENGTH</th>
                <th class="text-left text-gray-800 font-semibold text-sm">UPLOADED DATE</th>
                <th class="text-left text-gray-800 font-semibold text-sm">STATUS</th>
                <th class="text-left text-gray-800 font-semibold text-sm">SHIBA RATING</th>
              </tr>
            </thead>
            <tbody class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
              <tr class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
                <td class="flex justify-center"><img src="../assets/photo.jpg" alt=""></td>
                <td class="text-left text-sm">Shiba Watch</td>
                <td>
                  <div class="flex justify-left">
                    <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                    <div class="w-3 h-3 bg-purple-700 rounded-full mx-2"></div>
                    <div class="w-3 h-3 bg-pink-500 rounded-full mx-1"></div>
                  </div>
                </td>
                <td class="text-green-500 text-left text-sm">8.0/10</td>
                <td class="text-left text-sm">25 Oct 2021</td>
                <td>
                  <div class="bg-green-600 rounded-sm flex justify-center text-white"><p>Presale</p></div>
                </td>
                <td class="text-green-500 text-center text-sm">8.6/10</td>
              </tr>
              <tr class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
                <td class="flex justify-center"><img src="../assets/photo.jpg" alt=""></td>
                <td class="text-left text-sm">Shiba Watch</td>
                <td class="text-left">N.A.</td>
                <td class="text-red-500 text-left text-sm">3.4/10</td>
                <td class="text-left text-sm">25 Oct 2021</td>
                <td>
                  <div class="bg-green-600 rounded-sm flex justify-center text-white"><p>Presale</p></div>
                </td>
                <td class="text-green-500 text-center text-sm">2/10</td>
              </tr>
              <tr class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
                <td class="flex justify-center"><img src="../assets/photo.jpg" alt=""></td>
                <td class="text-left text-sm">Shiba Watch</td>
                <td>
                  <div class="flex justify-left">
                    <div class="w-3 h-3 bg-green-500 rounded-full"></div>
                  </div>
                </td>
                <td class="text-yellow-500 text-left text-sm">6.4/10</td>
                <td class="text-left text-sm">25 Oct 2021</td>
                <td>
                  <div class="bg-yellow-600 rounded-sm flex justify-center text-white"><p>Launched</p></div>
                </td>
                <td class="text-yellow-500 text-center text-sm">6/10</td>
              </tr>
              <tr class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
                <td class="flex justify-center"><img src="../assets/photo.jpg" alt=""></td>
                <td class="text-left text-sm">Shiba Watch</td>
                <td>
                  <div class="flex justify-left">
                    <div class="w-3 h-3 bg-purple-700 rounded-full"></div>
                  </div>
                </td>
                <td class="text-green-600 text-left text-sm">9.0/10</td>
                <td class="text-left text-sm">25 Oct 2021</td>
                <td>
                  <div class="bg-yellow-600 rounded-sm flex justify-center text-white"><p>Launched</p></div>
                </td>
                <td class="text-green-500 text-center text-sm">9.2/10</td>
              </tr>
              <tr class="border-b-2 bg-white border-gray-300 border-t-2 border-gray-300">
                <td class="flex justify-center"><img src="../assets/photo.jpg" alt=""></td>
                <td class="text-left text-sm">Shiba Watch</td>
                <td>
                  <div class="flex justify-left">
                    <div class="w-3 h-3 bg-pink-500 rounded-full"></div>
                  </div>
                </td>
                <td class="text-yellow-500 text-left text-sm">5/10</td>
                <td class="text-left text-sm">25 Oct 2021</td>
                <td>
                  <div class="bg-blue-600 rounded-sm flex justify-center text-white"><p>Private</p></div>
                </td>
                <td class="text-yellow-500 text-center text-sm">6.1/10</td>
              </tr>
            </tbody>
          </table>
          <div class="flex justify-between mt-5 mx-5 pb-5">
            <div class="flex">
              <div class="w-7 h-6 bg-gray-300 text-center text-blue-500 cursor-pointer">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
              </div>
              <p class="mx-2 text-sm text-gray-500">1-5 of 5</p>
              <div class="w-7 h-6 bg-gray-300 text-blue-500 cursor-pointer">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
              </div>
            </div>
            <div class="flex">
              <p class="mx-10 text-sm text-gray-500">Rows per page: <span class="text-black">5</span></p>
              <p class="mx-10 text-sm text-gray-500">1-5 of 5</p>
              <p class="flex mt-1 cursor-pointer">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
              </p>
            </div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  components: {
    Multiselect
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
