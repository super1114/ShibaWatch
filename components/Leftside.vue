<template>
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
</template>

<script>
  export default {
    methods: {
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
    }
    }
  }
</script>
<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>
<style scoped>
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
