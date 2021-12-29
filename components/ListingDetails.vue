<template>
  <div class="bg-gray-200 w-screen h-full relative" :class="is_mobile?'block':'grid grid-cols-4'">
    <Leftside />
    <div class="border-2 border-gray-200" :class="this.is_mobile?'col-span-4':'col-span-3'">
      <Topside />
      <div :class="this.is_mobile?'block':'grid gird-cols-3 gap-4 mt-5'">
        <div class="col-start-1 col-end-3 ml-3">
          <p class="font-bold text-2xl text-gray-600">Listing Details</p>
          <div class="bg-white pl-5 rounded-md pb-3">
            <div class="flex items-center">
              <div class="">
                <img :src="this.coin?`https://api.shibawatch.net/api/image_view/${this.coin.image}`:`../assets/avatar.jpg`" class="rounded-full ml-5 w-10 h-10" alt="">
              </div>
              <div class="ml-4">
                <div class="flex mt-5">
                  <p class="font-bold mt-1 text-xl">{{this.coin?this.coin.name:'None'}}</p>
                  <div class="ml-3 px-3 py-1 rounded-full bg-gray-300 text-blue-500">${{this.coin?this.coin.symbol:'None'}}</div>
                </div>
                <div class="flex mt-5">
                  <div class="px-3 py-1 rounded-full bg-red-200 text-red-700">Launched</div>
                </div>
              </div>
            </div>
            <div class="text-gray-700 flex gap-1 justify-center border-2 border-dashed bg-gray-200 py-3 px-3 mr-4 rounded-md mt-5">
              <div class="text-sm mt-1">Status <span class="text-sm px-2 py-1 rounded-full bg-green-200 text-green-500">Listed</span></div>
              <div class="text-sm mt-1">Network
                <span v-if="this.coin&&this.coin.chain!=''" class="text-sm px-2 py-1 rounded-full bg-green-200 text-green-500">
                  {{this.coin?this.coin.chain:'loading'}}
                </span>
                <span v-else class="text-sm px-2 py-1 rounded-full bg-green-200 text-green-500">
                  NONE
                </span>
              </div>
            </div>
            <div class="text-gray-700 flex gap-1 justify-center border-2 border-dashed bg-gray-200 py-3 px-3 mr-4 rounded-md mt-5">
              <div class="text-sm mt-1">Contract
                <span class="text-sm px-2 py-1 rounded-full bg-green-200 text-green-500">
                  {{this.coin?this.coin.contract:'loading'}}
                </span>
              </div>
            </div>
            <div class="bg-gray-200 border-2 border-gray-300 rounded-md mr-3 mt-5 pl-3 pr-4 pt-2 mb-5 text-gray-500 pb-3">
              <p v-if="this.coin" class="text-center">{{this.coin.description=='' ? 'No description provided' : this.coin.description}}</p>
              <p v-else class="text-center">loading</p>
            </div>
          </div>
        </div>
        <div class="col-start-3 col-end-4 mr-2">

          <div class="bg-white rounded-md mt-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">Links</p>
              <SvgIcon text="links" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <a v-if="this.coin&&this.coin.website" class="ml-5 mt-5 flex" :href="this.coin?this.coin.website:''" target="_blank">
              <SvgIcon text="website" />
              <span class="text-sm mt-1 ml-2">Website</span>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <span class="text-sm mt-1 ml-10" >Visit website</span>
              <SvgIcon text="visit1" />
            </a>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <a v-if="this.coin&&this.coin.telegram" class="ml-5 mt-5 flex" :href="this.coin?this.coin.telegram:''" target="_blank">
              <SvgIcon text="telegram" />
              <span class="text-sm mt-1 ml-2">Telegram</span>
              <span class="text-sm mr-3 ml-4 mt-1">:</span>
              <span class="text-sm mt-1 ml-10">Join Telegram</span>
              <SvgIcon text="visit2" />
            </a>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <a v-if="this.coin&&this.coin.twitter" class="ml-5 mt-5 flex pb-5" :href="this.coin?this.coin.twitter:''" target="_blank">
              <SvgIcon text="twitter" />
              <span class="text-sm mt-1 ml-2 mr-1">Twitter</span>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <span class="text-sm mt-1 ml-10">Follow Twitter</span>
              <SvgIcon text="visit3" />
            </a>
          </div>
          <!-- <div class="bg-white rounded-md mt-5 pb-5">
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
          </div> -->
          <div v-if="this.coin&&(this.coin.chart||this.coin.exchange)" class="bg-white rounded-md mt-5 pb-5">
            <div class="flex justify-between gap-20">
              <p class="mt-5 ml-5">Charts/Swap</p>
              <SvgIcon text="charts_swap" />
            </div>
            <div class="mx-5 mt-4 border-b-2 border-gray-400"></div>
            <a v-if="this.coin&&this.coin.exchange" class="ml-5 mt-5 flex" :href="this.coin?this.coin.exchange:''" target="_blank">
              <SvgIcon text="marketcap" />
              <span class="text-sm mt-1 ml-2">Exchange</span>
              <span class="text-sm mr-3 ml-6 mt-1">:</span>
              <span class="text-sm mt-1">Visit Exchange</span>
              <SvgIcon text="visit4" />
            </a>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <a v-if="this.coin&&this.coin.chart" class="ml-5 mt-5 flex" :href="this.coin?this.coin.chart:''" target="_blank">
              <SvgIcon text="charts" />
              <span class="text-sm mt-1 ml-2 mr-1">Charts</span>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <span class="text-sm mt-1 mr-1">View Charts</span>
              <SvgIcon text="visit5" />
            </a>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <!-- <div class="ml-5 mt-5 flex">
              <SvgIcon text="buynow" />
              <p class="text-sm mt-1 ml-2 -mr-3">Buy Now</p>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <p class="text-sm mt-1 mr-5">Buy Now</p>
              <SvgIcon text="visit6" />
            </div> -->
            <!-- <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="buynow" />
              <p class="text-sm mt-1 ml-2 -mr-3">Buy Now</p>
              <span class="text-sm mr-3 ml-20 mt-1">:</span>
              <button type="button" class="text-sm mt-1 bg-purple-700 rounded-full py-2 text-white flex">
                <p class="ml-2">$</p>
                <p class="ml-3">Flooze.Trade</p>
                <SvgIcon text="flooze" />
              </button>
            </div> -->
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
              <p class="text-sm mt-1 text-blue-500">{{this.coin?new Date(this.coin.uploaded_date).toLocaleDateString():''}}</p>
            </div>
            <div class="border-b-2 border-gray-200 mx-5 mt-2"></div>
            <div class="ml-5 mt-5 flex">
              <SvgIcon text="launch" />
              <p class="text-sm mt-1 ml-2">Launch</p>
              <span class="text-sm mr-3 ml-5 mt-1">:</span>
              <p class="text-sm mt-1 text-blue-500">{{this.coin?new Date(this.coin.launch_date).toLocaleDateString():''}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SvgIcon from '../components/SvgIcon'
import Leftside from './Leftside'
import Topside from './Topside'
import axios from "axios"

export default {
  components: {
    SvgIcon: SvgIcon,
    Leftside: Leftside,
    Topside: Topside
  },
  props:{
    id:Number
  },
  data() {
    return {
      value: [],
      options: ['Listings', 'Audit', 'KYC', 'ShibaWatch Swap'],
      is_mobile: false,
      coin: {}
    }
  },
  mounted() {
    if(window.innerWidth<1024) {
      this.is_mobile = true;
    }
  },
  async created() {
    const {data} = await axios(`https://api.shibawatch.net/api/detail/${this.id}`);
    console.log(data.result);
    if(data.result.length>0) this.coin = data.result[0];
  },
  methods: {

  }
}
</script>

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
