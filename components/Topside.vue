<template>
  <div class="w-full bg-white -mx-2 flex justify-between border-2 border-gray-300">
    <div></div>
    <div class="flex">
      <!-- <button type="button" class="bg-purple-800 mx-1 px-5 py-2 mt-6 mb-6 text-white rounded-lg cursor-pointer focus:outline-none" @click="signin">Sign In</button> -->
      <a v-if="!web3Injected" target="_blank" href="https://metamask.io/" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" >Install Metamask</a>
      <div v-else-if="account" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">{{this.account.substring(0,6)+"..."+this.account.substring(this.account.length-4,this.account.length)}}</div>
      <div v-else class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" @click="connectWallet">Connect Wallet</div>
    </div>
  </div>
</template>

<script>
import Web3 from "web3";
import Web3Modal from "web3modal";
import WalletConnectProvider from "@walletconnect/web3-provider";
import Fortmatic from 'fortmatic';
import ShibaJson from "../contract/ShibaWatch.json"
import BusdJson from "../contract/BUSD.json"




export default {
  name:"Topside",
  computed:{
    web3Injected() {
      if(typeof web3 == 'undefined') return false;
      else return true;
    }
  },
  data() {
    return {
      account:null,
      web3Obj: new Web3(Web3.givenProvider || 'https://bsc-dataseed.binance.org'),
      busdBalance: 0,
      shibaBalance: 0,
      shibaContractAddress: "0x52941a733F7bAb6E52d5c8f2045c9D9D9eA246Ff",
      busdContractAddress: "0xe9e7cea3dedca5984780bafc599bd69add087d56",
      shibaContract: null,
      busdContract: null,
      shibaAbi: ShibaJson.abi,
      busdAbi: BusdJson.abi,
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
      }, // required
    });
  },
  methods: {
    async networkChanged(networkId){
      this.networkId = networkId;
      if(networkId==56){
        if(this.account==null) return;
        this.web3Obj = new Web3('https://bsc-dataseed.binance.org');
        this.shibaContract = new this.web3Obj.eth.Contract(this.shibaAbi,Web3.utils.toChecksumAddress(this.shibaContractAddress));
        const res1 = await this.shibaContract.methods.balanceOf(this.account).call();
        console.log(res1);
        this.shibaBalance = Math.round(100*Web3.utils.fromWei(res1, 'ether'))/100;
        this.busdContract = new this.web3Obj.eth.Contract(this.busdAbi,Web3.utils.toChecksumAddress(this.busdContractAddress));
        const res2 = await this.busdContract.methods.balanceOf(this.account).call();
        this.busdBalance = Math.round(100*Web3.utils.fromWei(res2, 'ether'))/100;
        await this.storeItem("shibaBalance", this.shibaBalance);
        await this.storeItem("busdBalance", this.busdBalance);
      } else {
        await this.switchNetwork();
      }
    },
    async storeItem(key, value) {
      if(process.client) {
        localStorage.setItem(key, value);
      }
    },
    removeItem(key) {
      if(process.client) {
        localStorage.removeItem(key);
      }
    },
    async getAccountData(provider) {
      const web3 = new Web3(provider);
      const accounts = await web3.eth.getAccounts();
      if(accounts.length>0) {
        this.account = accounts[0];
        await this.networkChanged(56);
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

      //document.location.reload();
    },
    async switchNetwork(){
      // await window.ethereum.request({
      //   method: 'wallet_switchEthereumChain',
      //   params: [{ chainId: "0x38" }],
      // });
    },
  }
}
</script>
