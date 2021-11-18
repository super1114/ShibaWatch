<template>
  <div class="grid grid-cols-4 bg-gray-200 w-screen h-full relative">
    <Leftside />
    <div class="col-start-2 col-end-5 border-2 border-gray-200">
      <Topside />
      <div class="grid gird-cols-3 gap-4 mt-5">
        <div class="col-start-1 col-end-3 ml-3">
          <p class="font-bold text-2xl text-gray-600">Listing Details</p>
          <div class="bg-white pl-5 rounded-md pb-3">
            <div class="flex">
              <div class="mt-5">
                <img src="../assets/star.png" class="rounded-full border-2 border-blue-600" alt="">
                <img src="../assets/avatar.jpg" class="rounded-full  -mt-3 ml-5" alt="">
              </div>
              <div class="ml-4">
                <div class="flex mt-5">
                  <p class="font-bold mt-1 text-xl">ShibaWatch</p>
                  <div class="ml-3 px-3 py-1 rounded-full bg-gray-300 text-blue-500">$SHIBAW</div>
                </div>
                <div class="flex mt-5">
                  <div class="px-3 py-1 rounded-full bg-red-200 text-red-700">Launched</div>
                  <p class="ml-3 mt-1">This project has launched.</p>
                </div>
              </div>
            </div>
            <div class="text-gray-700 flex gap-1 justify-between border-2 border-dashed border-gray-300 bg-gray-200 py-3 px-3 mr-4 rounded-md mt-5">
              <p class="text-sm mt-1">Status</p>
              <div class="text-sm px-2 py-1 rounded-full bg-green-200 text-green-500">Listed</div>
              <p class="text-sm mt-1">Votes for Listing</p>
              <div class="text-sm px-2 py-1 rounded-full bg-purple-200 text-purple-500">500/500</div>
              <p class="text-sm mt-1">Votes</p>
              <div class="text-sm px-2 py-1 rounded-full bg-orange-300 text-orange-500">15452</div>
              <p class="text-sm mt-1">Votes Today</p>
              <div class="text-sm px-2 py-1 rounded-full bg-blue-200 text-blue-500">1545</div>
              <p class="text-sm mt-1">Network</p>
              <div class="text-sm px-2 py-1 rounded-full bg-gray-500 text-gray-700">BSC</div>
            </div>
            <div class="bg-gray-200 border-2 border-gray-300 rounded-md mr-3 mt-5 pl-3 pr-4 pt-2 mb-5 text-gray-500 pb-3">
              <p>Shiba Watch is a multi-faunctional platform that aims to provide a safe space for investors to invest in. The platform will list upcoming new tokens that are launched or in its early stage.</p>
              <p>Several metrics will be shown to guide investors on whether the token is safe to invest in. These metrics include social media strength, rating, review and indication of whether the team is KYC verified.</p>
              <p>When awareness of scams is build, potential investors will be inclined to invest more in cryptocurrency.</p>
              <p>The next feature of the platform will inculde an NFT marketplace. Users of Shiba Watch platform will be able to mint, purchase and sell their NFTs.</p>
              <p>Users will be able to stake their tokens in Shiba Watch pools which grants APY (Annual Percentage Yield). The de-fi lending feature will provide flash and micro loans to users</p>
              <p>and a collateral will have to be placed to ensure lower rate of default.</p>
            </div>
          </div>
        </div>
        <div class="col-start-3 col-end-4 mr-2">
          <p class="font-bold text-2xl text-gray-600">Popularity</p>
          <div class="bg-white rounded-md">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">WatchLists</p>
              <SvgIcon text="star" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <div class="text-center mt-5 pb-5">
              <p class="text-2xl font-bold text-yellow-600">4039</p>
              <p>WatchLists</p>
            </div>
          </div>
          <div class="bg-white rounded-md mt-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">Links</p>
              <SvgIcon text="links" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="website" />
              <p class="text-sm mt-1 ml-2">Website</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 ml-10">Visit website</p>
              <SvgIcon text="visit1" />
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="telegram" />
              <p class="text-sm mt-1 ml-2">Telegram</p>
              <span class="text-sm mr-3 ml-4 mt-1">:</span>
              <p class="text-sm mt-1 ml-10">Join Telegram</p>
              <SvgIcon text="visit2" />
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex pb-5">
              <SvgIcon text="twitter" />
              <p class="text-sm mt-1 ml-2 mr-1">Twitter</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 ml-10">Follow Twitter</p>
              <SvgIcon text="visit3" />
            </div>
          </div>
          <div class="bg-white rounded-md mt-5 pb-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">Price</p>
              <SvgIcon text="price" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="marketcap" />
              <p class="text-sm mt-1 ml-2">Marketcap</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">$2,069,028</p>
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="usd1" />
              <p class="text-sm mt-1 ml-2">Price(USD)</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">$0.00000000320363</p>
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="usd2" />
              <p class="text-sm mt-1 ml-2">Price(USD)</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">$600.07</p>
            </div>
          </div>
          <div class="bg-white rounded-md mt-5 pb-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">Charts/Swap</p>
              <SvgIcon text="charts_swap" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="marketcap" />
              <p class="text-sm mt-1 ml-2">Coin Marketcap</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1">CoinMarketCap</p>
              <SvgIcon text="visit4" />
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="charts" />
              <p class="text-sm mt-1 ml-2 mr-1">Charts</p>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <p class="text-sm mt-1 mr-1">View Charts</p>
              <SvgIcon text="visit5" />
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="buynow" />
              <p class="text-sm mt-1 ml-2 -mr-3">Buy Now</p>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <p class="text-sm mt-1 mr-5">Buy Now</p>
              <SvgIcon text="visit6" />
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="buynow" />
              <p class="text-sm mt-1 ml-2 -mr-3">Buy Now</p>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <button type="button" class="text-sm mt-1 bg-purple-700 rounded-full py-2 text-white flex">
                <p class="ml-2">$</p>
                <p class="ml-3">Flooze.Trade</p>
                <SvgIcon text="flooze" />
              </button>
            </div>
          </div>
          <div class="bg-white rounded-md mt-5 mb-4 pb-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">information</p>
              <SvgIcon text="info" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="added" />
              <p class="text-sm mt-1 ml-2">Added</p>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">Obtober 27 2021</p>
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="launch" />
              <p class="text-sm mt-1 ml-2">Launch</p>
              <span class="text-sm mr-3 ml-5 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">October 27 2021</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'
import SvgIcon from '../components/SvgIcon'
import Leftside from './Leftside'
import Topside from './Topside'

export default {
  components: {
    Multiselect,
    SvgIcon: SvgIcon,
    Leftside: Leftside,
    Topside: Topside
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
