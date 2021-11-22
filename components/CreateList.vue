<template>
  <div class="grid grid-cols-4 bg-gray-200 w-full h-full relative">
    <Leftside />
    <div class="col-start-2 col-end-5 border-2 border-gray-200">
      <Topside />
      <div class="bg-white ml-5 mr-10 mt-10 mb-10 rounded-md px-10">
        <div class="py-10">
          <p class="font-bold text-3xl">Submit new coin</p>
          <p>Please fill out this form carefully to add new coin to <span class="text-blue-500">CoinSniper</span>.After submission, your coin will be visible on the <span class="text-blue-500">New Listings</span> page.Get 500 votes to be officially listed on <span class="text-blue-500">CoinSniper</span>.</p>
        </div>
        <div  class="grid grid-cols-4 gap-10">
          <div v-if="!file" class="col-start-1 col-end-2">
            <p class="text-2xl">Upload Logo*</p>
            <input type="file" ref="file" style="display: none" @change="changeFile">
            <div class="bg-gray-300 w-60 h-100 rounded-lg cursor-pointer" @click="$refs.file.click()">
              <svg xmlns="http://www.w3.org/2000/svg" class="font-semibold h-13 w-13 text-blue-500 mt-3 py-10 mx-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12" />
              </svg>
              <p class="text-center -mt-10 text-2xl">Upload Image</p>
              <div class="invisible mt-5">space</div>
            </div>
          </div>
          <div v-else class="col-start-1 col-end-2">
            <p class="text-2xl">Upload Logo*</p>
            <div class="bg-gray-300 mt-2 py-10 w-60 h-100 rounded-lg cursor-pointer" @click="$refs.file.click()">
              <p class="text-center py-10 text-2xl">{{this.file.name}}</p>
            </div>
          </div>
          <div class="col-start-2 col-end-5">
            <div class="mt-3">
              <p class="text-xl text-gray-700">Name*</p>
              <input type="text" v-model="name" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="Shiba Watch">
            </div>
            <div class="mt-6">
              <p class="text-xl text-gray-700">Symbol*</p>
              <input type="text" v-model="sym" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="SHIBAW">
            </div>
            <div class="mt-6">
              <p class="text-xl text-gray-700">Network/Chain</p>
              <Multiselect v-model="chain" :options="chain_option" class="placeholder-opacity-100 cursor-pointer " :multiple="false" placeholder="Binance Smart Chain(BSC)"></Multiselect>
            </div>
          </div>
        </div>
        <div>
          <p class="mt-10 text-lg">Project in presale phases?</p>
          <div class="mt-5">
            <label for="No">
              <input type="radio" name="radio1" value="No" id="No" @change="$emit('input', 'No')" @click="presale_no" />
              No
            </label>
            <label for="Yes">
              <input type="radio" name="radio1" value="Yes" id="Yes" @change="$emit('input', 'Yes')" @click="presale_yes" />
              Yes
            </label>
            <div v-if="presale">
              <div class="mt-5 text-lg">
                <p>Contract Address*</p>
                <input type="text" v-model="contract"  class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
              </div>
              <div class="mt-5 text-lg">
                <p>Description*</p>
                <textarea rows="3" class="px-2 form-area mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 focus:outline-none placeholder-opacity-100" placeholder="Describe your token here in detail."></textarea>
              </div>
            </div>
            <div v-else>
              <div class="mt-5">
                <div class="rounded-md bg-purple-700 w-full flex justify-center">
                  <div class="mt-10 mb-10">
                    <p class="text-white">Planning your presale or fair launch?</p>
                    <p class="text-white">Consider our official launchpad partner!</p>
                    <button type="button" class="focus:outline-none rounded bg-white flex justify-center text-purple-700 mt-5 px-3 py-1 ">Contact Us For More Information</button>
                  </div>
                </div>
                <p class="text-lg mt-5">Contract Address(Optional for Presale)</p>
                <input type="text" v-model="contract"  class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                <p class="mt-3 text-gray-600">Your contract address will be hidden until your presale is finished.</p>
              </div>
              <div class="mt-5 text-lg">
                <p>Presale link(Optional)</p>
                <input type="text" v-model="presale_link" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
              </div>
              <div class="mt-5 text-lg">
                <p>Description*</p>
                <input type="text" v-model="desc" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="mt-5">
            <p class="text-lg">Is project audited?</p>
            <div class="mt-5">
              <label for="au_No">
                <input type="radio" name="radio2" value="au_No" id="au_No" @change="$emit('input', 'au_No')" @click="audit_no" />
                No
              </label>
              <label for="au_Yes">
                <input type="radio" name="radio2" value="au_Yes" id="au_Yes" @change="$emit('input', 'au_Yes')" @click="audit_yes" />
                Yes
              </label>
              <div v-if="audit">
                <div class="mt-5 text-lg">
                  <p>Link to Audit</p>
                  <input type="text" v-model="audit_link" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                </div>
              </div>
            </div>
          </div>
          <div class="mt-5">
            <p class="text-lg">Is team KYC?</p>
            <div class="mt-5">
              <label for="kyc_No">
                <input type="radio" name="radio3" value="kyc_No" id="kyc_No" @change="$emit('input', 'kyc_No')" @click="kyc_no" />
                No
              </label>
              <label for="kyc_Yes">
                <input type="radio" name="radio3" value="kyc_Yes" id="kyc_Yes" @change="$emit('input', 'kyc_Yes')" @click="kyc_yes" />
                Yes
              </label>
              <div v-if="kyc">
                <div class="mt-5 text-lg">
                  <p>KYC Proof Link</p>
                  <input type="text" v-model="kyc_link" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                </div>
              </div>
            </div>
          </div>
          <div class="mt-5">
            <p class="text-lg">Is team doxxed?</p>
            <div class="mt-5">
              <label for="dox_No">
                <input type="radio" name="radio4" value="dox_No" id="dox_No" @change="$emit('input', 'dox_No')" @click="dox_no" />
                No
              </label>
              <label for="dox_Yes">
                <input type="radio" name="radio4" value="dox_Yes" id="dox_Yes" @change="$emit('input', 'dox_Yes')" @click="dox_yes" />
                Yes
              </label>
              <div v-if="dox">
                <div class="mt-5 text-lg">
                  <p>Dox Proof Link</p>
                  <input type="text" v-model="dox_link" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                </div>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="mt-5 text-lg">
            <p>Chart(Optional)</p>
            <input type="text" v-model="chart" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Exchange(Optional)</p>
            <input type="text" v-model="exchange" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Website</p>
            <input type="text" v-model="website" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="https://app.shibawatch.net">
          </div>
          <div class="mt-5 text-lg">
            <p>Launch Date*</p>
            <input type="date" v-model="launch_date" class="mt-2 rounded-md bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Telegram Link*</p>
            <input type="text" v-model="telegram" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Twitter Link</p>
            <input type="text" v-model="twitter" class="px-2 mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <button type="button" class="mt-10 bg-purple-700 hover:bg-purple-800 rounded-md py-3 px-6 text-white focus:outline-none">Add Link</button>
          <div class="flex mt-10">
            <input type="radio" class="mt-2" :checked="agreeTerms" @change="changeAgree">
            <p class="mx-2">I agree to the <span class="text-blue-500 cursor-pointer">Terms and Conditions*</span></p>
          </div>
          <button type="button" class="mt-10 mb-10 bg-purple-700 hover:bg-purple-800 rounded-md py-3 px-6 text-white focus:outline-none" @click="submitCoin">Submit Coin</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'
import Leftside from './Leftside'
import Topside from './Topside'
import axios from "axios";
export default {
  components: {
    Multiselect,
    Leftside,
    Topside
  },
  data() {
    return {
      file:null,
      name:"",
      sym:"",
      contract:"",
      desc:"",
      presale_link:"",
      audit_link:"",
      kyc_link:"",
      dox_link:"",
      chart:"",
      exchange:"",
      website:"",
      launch_date:"",
      telegram:"",
      twitter:"",
      additional_link:"",
      presale: true,
      audit: false,
      kyc: false,
      dox: false,
      value: [],
      chain: [],
      options: ['Listings', 'Audit', 'KYC', 'ShibaWatch Swap'],
      chain_option: ['Ethereum', 'BSC', 'Polygon'],
      agreeTerms:false
    }
  },
  methods: {
    changeAgree() {
      this.agreeTerms = !this.agreeTerms;
    },
    changeFile(event) {
      this.file = event.target.files[0];
    },
    async submitCoin() {
      if(!this.agreeTerms) {
        alert("You need to agree Terms and Conditions")
        return;
      }if(this.name==""||this.sym=="") {
        alert("Coin name and symbol is required");
        return;
      }
      let formdata = new FormData();
      formdata.append("name", this.name);
      formdata.append("symbol", this.sym);
      formdata.append("file", this.file);
      formdata.append("contract", this.contract);
      formdata.append("chain", this.chain);
      formdata.append("description", this.desc);
      formdata.append("presale_link", this.presale_link);
      formdata.append("audit_link", this.audit_link);
      formdata.append("kyc_link", this.kyc_link);
      formdata.append("dox_link", this.dox_link);
      formdata.append("chart", this.chart);
      formdata.append("exchange", this.exchange);
      formdata.append("website", this.website);
      formdata.append("launch_date", this.launch_date);
      formdata.append("telegram", this.telegram);
      formdata.append("twitter", this.twitter);
      formdata.append("additional_link", this.additional_link);
      const { data } = await axios.post('http://localhost:3030/api/create_coin',formdata,{
        headers: {
          'Content-Type': 'multipart/form-data'
        }
      });
      if(data.status==true) {
        alert(data.message);
        document.location = "/";
      }
    },
    presale_yes() {
      this.presale = false;
    },
    presale_no() {
      this.presale = true;
    },
    audit_no() {
      this.audit = false;
    },
    audit_yes() {
      this.audit = true;
    },
    kyc_no() {
      this.kyc = false;
    },
    kyc_yes() {
      this.kyc = true;
    },
    dox_no() {
      this.dox = false;
    },
    dox_yes() {
      this.dox = true;
    }
  }
}

</script>

<style>

</style>
