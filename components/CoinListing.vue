<template>
  <div v-if="!this.loading" class="bg-gray-200 w-screen h-screen relative" :class="is_mobile?'block':'grid grid-cols-4'">
    <Leftside />
    <div :class="this.is_mobile?'col-span-4':'col-span-3'">
      <Topside />
      <div class="flex justify-between items-center pr-2">
        <div>
          <p class="font-bold mt-3 mx-5 text-3xl">Listings</p>
          <p class="pl-5 mt-2 font-semibold text-gray-700">We collate and streamline all existing and upcoming coins all in one  listing</p>
        </div>
        <a href="/create" class="flex bg-purple-800 text-white px-2 py-2 rounded-lg cursor-pointer">
          <SvgIcon text="plus" />
          <p :class="this.is_mobile?'hide_sidebar':''">Create Listing</p>
        </a>
      </div>
      <div class="bg-white  mt-1 rounded-md">
        <div class="mt-3 pt-2" :class="is_mobile?'':'flex'">
          <div class="flex mt-3 ml-5" :class="is_mobile?'justify-center':''">
            <div class="flex border-2 rounded h-8">
                <button class="flex items-center justify-center pl-2 bg-white">
                    <SvgIcon text="search" />
                </button>
                <input v-on:keyup.enter="getData" type="text" class="px-2 py-2 w-80 focus:outline-none" v-model="searchkey" placeholder="Search...">
            </div>
          </div>
          <div class="flex justify-center">
            <div class="flex">
              <div class="w-3 h-3 rounded-full bg-green-500 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">Audited</p>
              <div class="w-3 h-3 rounded-full bg-purple-700 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">KYC</p>
              <div class="w-3 h-3 rounded-full bg-pink-500 mt-6 mx-3"></div>
              <p class="mt-5 -mx-2 text-xs">Doxxed</p>
            </div>
          </div>
        </div>
        <table class="table-auto mt-5 w-full p-10">
            <thead class="border-b-2 bg-gray-200 border-gray-300 border-t-2 border-gray-300">
              <tr>
                <th class="invisible bg-gray-300">avatar</th>
                <th class="text-center text-gray-800 font-semibold text-sm">NAME</th>
                <th class="text-center text-gray-800 font-semibold text-sm">METRICS</th>
                <th class="text-center text-gray-800 font-semibold text-sm" :class="this.is_mobile?'hide_sidebar':''">SOCIAL MEDIA STRENGTH</th>
                <th class="text-center text-gray-800 font-semibold text-sm" :class="this.is_mobile?'hide_sidebar':''">UPLOADED DATE</th>
                <th class="text-center text-gray-800 font-semibold text-sm" :class="this.is_mobile?'hide_sidebar':''">STATUS</th>
                <th class="text-center text-gray-800 font-semibold text-sm">TOKEN RATING</th>
              </tr>
            </thead>
            <tbody class="border-b-2 bg-white border-gray-300 border-t-2">
              <tr v-if="coins.length==0" class="border-b-2 bg-white border-gray-300 border-t-2">
                <td class="text-center text-sm" colspan="7">
                  No coins find.
                </td>
              </tr>
              <tr v-else v-for="index in 5" :key="index" class="border-b-2 bg-white border-gray-300 border-t-2" @click="gotoDetail(coins[curPage*5+index-1])">
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'" class="flex justify-center py-1">
                  <img :src="'https://api.shibawatch.net/api/image_view/'+coins[curPage*5+index-1].image" class="w-10 h-10"
                  >
                </td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'" class="text-center text-sm">{{coins[curPage*5+index-1].name}}</td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'">
                  <div v-if="coins[curPage*5+index-1].audit_link==''&&coins[curPage*5+index-1].doxxed_link==''&&coins[curPage*5+index-1].kyc_link==''" class="text-center">N.A.</div>
                  <div class="flex justify-center">
                    <div v-if="coins[curPage*5+index-1].audit_link!=''" class="w-3 h-3 bg-green-500 rounded-full"></div>
                    <div v-if="coins[curPage*5+index-1].kyc_link!=''" class="w-3 h-3 bg-purple-700 rounded-full mx-2"></div>
                    <div v-if="coins[curPage*5+index-1].doxxed_link!=''" class="w-3 h-3 bg-pink-500 rounded-full mx-1"></div>
                  </div>
                </td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'" class="text-green-500 text-center text-sm" :class="is_mobile?'hide_sidebar':''">{{coins[curPage*5+index-1].social}}</td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'" :class="is_mobile?'hide_sidebar':''" class="text-center text-sm">{{new Date(coins[curPage*5+index-1].uploaded_date).toLocaleDateString()}}</td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'" :class="is_mobile?'hide_sidebar':''">
                  <div class="bg-green-600 rounded-sm flex justify-center text-white">Presale</div>
                </td>
                <td v-if="typeof coins[curPage*5+index-1]!='undefined'"  class="text-green-500 text-center text-sm">
                  {{coins[curPage*5+index-1].token_score}}
                </td>
              </tr>
            </tbody>
          </table>
          <div class="flex justify-between mt-5 mx-5 pb-5">
            <div class="flex">
              <div class="w-7 h-6 bg-gray-300 text-center text-blue-500 cursor-pointer" @click="prevPage">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
                </svg>
              </div>
              <p class="mx-2 text-sm text-gray-500">{{startCount}}-{{endCount}} of {{coins.length}}</p>
              <div class="w-7 h-6 bg-gray-300 text-blue-500 cursor-pointer" @click="nextPage">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                </svg>
              </div>
            </div>
            <div class="flex">
              <p class="mx-10 text-sm text-gray-500">Rows per page: <span class="text-black">5</span></p>
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
    SvgIcon,
    Leftside,
    Topside
  },
  computed: {
    pageCount() {
      return Math.round(this.coins.length / 5)
    },
    startCount() {
      if(this.coins.length==0) return 0;
      return this.curPage*5+1;
    },
    endCount(){
      if(this.coins.length == 0) return 0;
      return (this.curPage+1)*5 > this.coins.length ? this.coins.length : (this.curPage+1)*5
    }
  },
  data() {
    return {
      value: [],
      options: ['Listings', 'Audit', 'KYC', 'ShibaWatch Swap'],
      coins:[],
      searchkey: "",
      curPage: 0,
      is_mobile:false,
      loading:true
    }
  },
  mounted() {
    if(window.innerWidth<1024) {
      this.is_mobile = true;
    }
    this.loading = false;
  },
  async created() {
    if (process.client) {
      if(window.innerWidth<1024) {
        this.is_mobile = true;
      }
    }
    this.getData();
  },
  methods: {
    getData() {
      axios({
        method: 'post',
        url: 'https://api.shibawatch.net/api/list',
        data: {
          key: this.searchkey
        }
      }).then(({data}) => {
        this.curPage = 0;
        this.coins = data.result;
      });
    },
    nextPage() {
      if(5*(this.curPage+1)>=this.coins.length) return;
      this.curPage++;
    },
    prevPage() {
      if(this.curPage==0) return;
      this.curPage--;
    },
    gotoDetail(tr) {
      document.location = "/detail/"+tr.id;
    }
  }
}
</script>
<style>
  .hide_sidebar {
    display: none;
  }
</style>
