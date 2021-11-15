<template>
  <div class="grid grid-cols-4 bg-gray-200 w-full h-full relative">
    <div class="col-start-1 col-end-2 bg-white mt-20 mb-10 px-5 rounded-tr-lg rounded-br-lg shadow-md sticky h-50">
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
          <div class="mt-3 hover:text-blue-600"><a href="#">ShibaWatch SWAP</a></div>
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
          <button type="button" class="bg-purple-800 mx-1 px-5 py-2 mt-6 mb-6 text-white rounded-lg cursor-pointer" @click="signin">Sign In</button>
          <div class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">Connect Wallet</div>
        </div>
      </div>

      <div class="bg-white ml-5 mr-10 mt-10 mb-10 rounded-md px-10">
        <div class="py-10">
          <p class="font-bold text-3xl">Submit new coin</p>
          <p>Please fill out this form carefully to add new coin to <span class="text-blue-500">CoinSniper</span>.After submission, your coin will be visible on the <span class="text-blue-500">New Listings</span> page.Get 500 votes to be officially listed on <span class="text-blue-500">CoinSniper</span>.</p>
        </div>
        <div class="grid grid-cols-4 gap-10">
          <div class="col-start-1 col-end-2">
            <p class="text-2xl">Upload Logo*</p>
            <div class="bg-gray-300 w-60 h-100 rounded-lg cursor-pointer">
              <svg xmlns="http://www.w3.org/2000/svg" class="font-semibold h-13 w-13 text-blue-500 mt-3 py-10 mx-10" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12" />
              </svg>
              <p class="text-center -mt-10 text-2xl">Upload Image</p>
              <div class="invisible mt-10">space</div>
            </div>
          </div>
          <div class="col-start-2 col-end-5">
            <div class="mt-3">
              <p class="text-xl text-gray-700">Name*</p>
              <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="Shiba Watch">
            </div>
            <div class="mt-6">
              <p class="text-xl text-gray-700">Symbol*</p>
              <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="SHIBAW">
            </div>
            <div class="mt-6">
              <p class="text-xl text-gray-700">Network/Chain</p>
              <Multiselect v-model="chain" :options="chain_option" class="placeholder-opacity-100 cursor-pointer " :multiple="true" placeholder="Binance Smart Chain(BSC)"></Multiselect>
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
                <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
              </div>
              <div class="mt-5 text-lg">
                <p>Description*</p>
                <textarea rows="3" class="form-area mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 focus:outline-none placeholder-opacity-100" placeholder="Describe your token here in detail."></textarea>
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
                <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                <p class="mt-3 text-gray-600">Your contract address will be hidden until your presale is finished.</p>
              </div>
              <div class="mt-5 text-lg">
                <p>Presale link(Optional)</p>
                <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
              </div>
              <div class="mt-5 text-lg">
                <p>Description*</p>
                <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
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
                  <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
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
                  <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
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
                  <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
                </div>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="mt-5 text-lg">
            <p>Chart(Optional)</p>
            <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Exchange(Optional)</p>
            <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Website</p>
            <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none placeholder-opacity-100" placeholder="https://app.shibawatch.net">
          </div>
          <div class="mt-5 text-lg">
            <p>Launch Date*</p>
            <input type="date" class="mt-2 rounded-md bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Telegram Link*</p>
            <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <div class="mt-5 text-lg">
            <p>Twitter Link</p>
            <input type="text" class="mt-2 rounded-md w-full bg-gray-100 border-2 border-gray-300 py-2 focus:outline-none">
          </div>
          <button type="button" class="mt-10 bg-purple-700 rounded-md py-3 px-6 text-white focus:outline-none">Add Link</button>
          <div class="flex mt-10">
            <input type="radio" class="mt-2">
            <p class="mx-2">I agree to the <span class="text-blue-500">Terms and Conditions*</span></p>
          </div>
          <button type="button" class="mt-10 mb-10 bg-purple-700 rounded-md py-3 px-6 text-white focus:outline-none">Submit Coin</button>
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
      presale: true,
      audit: false,
      kyc: false,
      dox: false,
      value: [],
      chain: [],
      options: ['Listings', 'Audit', 'KYC', 'ShibaWatch Swap'],
      chain_option: ['Ethereum', 'BSC', 'Polygon']
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
