<template>
  <div class="grid grid-cols-4 bg-gray-200 w-screen h-full relative">
    <Leftside />
    <div class="col-start-2 col-end-5 border-2 border-gray-200">
      <div class="w-full bg-white -mx-2 flex justify-between border-2 border-gray-300">
        <div></div>
        <div class="flex">
          <a v-if="!web3Injected" target="_blank" href="https://metamask.io/" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" >Install Metamask</a>
          <div v-else-if="account" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">{{this.account.substring(0,6)+"..."+this.account.substring(this.account.length-4,this.account.length)}}</div>
          <div v-else class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" @click="connectWallet">Connect Wallet</div>
        </div>
      </div>
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
                <p>${{this.shibaBalance}}</p>
              </div>
              <div class="bg-yellow-600 text-gray-700 py-6 px-2 mr-10 rounded">
                <div class="bg-white -mt-10 float-right">
                  <img src="../assets/busd.png" class="rounded-full" alt="">
                </div>
                <p class="mx-10">${{this.busdBalance}}</p>
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
                  <p class="mx-4">${{this.pending}}</p>
                </div>
              </div>
              <div>
                <p class="-mt-10 mb-3 font-bold text-lg">Total</p>
                <div class="bg-pink-200 text-pink-700 py-6 px-2 mr-10 rounded">
                  <div class="bg-white -mt-10 float-right">
                    <img src="../assets/busd.png" class="rounded-full" alt="">
                  </div>
                  <p class="mx-10">${{this.total}}</p>
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
              <p class="text-xl text-yellow-500 font-semibold">${{this.totalDistributed}}</p>
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
            <p class="text-gray-500">0xe9e7cea3dedca5984780bafc599bd69add087d56</p>
            <SvgIcon text="busd_copy" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SvgIcon from './SvgIcon';
import Leftside from './Leftside'
import Web3 from "web3";
import Web3Modal from "web3modal";
import WalletConnectProvider from "@walletconnect/web3-provider";
import Fortmatic from 'fortmatic';
import ShibaJson from "../contract/ShibaWatch.json"
import BusdJson from "../contract/BUSD.json"
import DividendDistributorJson from "../contract/DividendDistributor.json"
export default {
  components: {
    SvgIcon,
    Leftside,
  },
  computed:{
    web3Injected() {
       return true;
    }
  },
  data() {
    return {
      value: [],
      account:null,
      web3Obj: new Web3(Web3.givenProvider || 'https://bsc-dataseed.binance.org'),
      busdBalance: 0,
      shibaBalance: 0,
      pending: 0,
      total: 0,
      totalDistributed: 0,
      shibaContractAddress: "0x52941a733F7bAb6E52d5c8f2045c9D9D9eA246Ff",
      busdContractAddress: "0xe9e7cea3dedca5984780bafc599bd69add087d56",
      shibaContract: null,
      busdContract: null,
      distributorContract: null,
      shibaAbi: ShibaJson.abi,
      busdAbi: BusdJson.abi,
      busdAbi: BusdJson.abi,
      DividendDistributorAbi: DividendDistributorJson.abi,
      networkId: "1",
      web3Modal:null
    }
  },
  async created() {
    this.web3Modal = new Web3Modal({
      cacheProvider: false, // optional
      providerOptions : {
        walletconnect: {
          package: WalletConnectProvider,
          options: {
            infuraId: "8043bb2cf99347b1bfadfb233c5325c0",
          }
        },
        fortmatic: {
          package: Fortmatic,
          options: {
            key: "pk_test_391E26A3B43A3350"
          }
        }
      }
    });
    this.web3Obj = new Web3('https://bsc-dataseed.binance.org');
    this.shibaContract = new this.web3Obj.eth.Contract(this.shibaAbi,Web3.utils.toChecksumAddress(this.shibaContractAddress));
    this.busdContract = new this.web3Obj.eth.Contract(this.busdAbi,Web3.utils.toChecksumAddress(this.busdContractAddress));
    this.distributorContract = new this.web3Obj.eth.Contract(this.DividendDistributorAbi, Web3.utils.toChecksumAddress("0x11ac188b5aa890026e084aac0d0fc6d4d1178933"));
    const res = await this.distributorContract.methods.totalDistributed().call();
    this.totalDistributed = Math.round(1000*Web3.utils.fromWei(res, 'ether'))/1000;
  },
  methods: {
    async networkChanged(){
      if(this.account==null) return;
      const res1 = await this.shibaContract.methods.balanceOf(this.account).call();
      this.shibaBalance = Math.round(100*Web3.utils.fromWei(res1, 'ether'))/100;
      const res2 = await this.busdContract.methods.balanceOf(this.account).call();
      this.busdBalance = Math.round(100*Web3.utils.fromWei(res2, 'ether'))/100;
      const res3 = await this.distributorContract.methods.getUnpaidEarnings(this.account).call();
      this.pending = Web3.utils.fromWei(res3, 'ether');
      const res4 = await this.distributorContract.methods.shares(this.account).call();
      console.log(res4);
      this.total = Web3.utils.fromWei(res4[2], 'ether');
    },
    async getAccountData(provider) {
      const web3 = new Web3(provider);
      const accounts = await web3.eth.getAccounts();
      if(accounts.length>0) {
        this.account = accounts[0];
        await this.networkChanged();
      }
    },
    async connectWallet() {
      try {
        const provider = await this.web3Modal.connect();
        await this.getAccountData(provider)
      } catch(e) {
        console.log("Could not get a wallet connection", e);
        return;
      }
    }
  }
}

</script>
