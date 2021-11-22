<template>
  <div class="w-full bg-white -mx-2 flex justify-between border-2 border-gray-300">
    <div></div>
    <div class="flex">
      <button type="button" class="bg-purple-800 mx-1 px-5 py-2 mt-6 mb-6 text-white rounded-lg cursor-pointer focus:outline-none" @click="signin">Sign In</button>
      <a v-if="!web3Injected" target="_blank" href="https://metamask.io/" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" >Install Metamask</a>
      <div v-else-if="account" class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer">{{this.account.substring(0,6)+"..."+this.account.substring(this.account.length-4,this.account.length)}}</div>
      <div v-else class="bg-purple-800 mt-6 mb-6 mx-5 text-white px-5 py-2 rounded-lg cursor-pointer" @click="connectWallet">Connect Wallet</div>
    </div>
  </div>
</template>

<script>
import Web3 from "web3";
import ShibaJson from "../contract/ShibaWatch.json"
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
      shibaContract: null,
      shibaAbi: ShibaJson.abi
    }
  },
  async created() {
    this.web3Obj.eth.getAccounts().then((result)=>{
      if(result.length>0) this.account = result[0];
    })
    //console.log(this.web3Obj.currentProvider);
    // this.shibaContract = new this.web3Obj.eth.Contract(this.shibaAbi,this.shibaContractAddress);
    // console.log(this.shibaContract);
    //console.log(this.shibaContract);

  },
  methods: {
    signin() {
      //console.log();
      document.location = '/login';
    },
    async connectWallet() {
      await window.ethereum.request({ method: 'eth_requestAccounts' }).then((result)=>{
        console.log("result="+result)
        document.location.reload();
      });
    }
  }
}

</script>

<style scoped>

</style>
