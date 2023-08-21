import Homepage from ''
<template>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Checkout</title>

        <link rel="stylesheet"
            href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
        
    </head>

    <body>
        <section class="h-screen bg-gray-100 py-12 sm:py-16 lg:py-20">
            <div class="mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex items-center justify-center">
                    <h1 class="text-2xl font-semibold text-gray-900">Your Cart</h1>
                </div>

                <div class="mx-auto mt-8 max-w-md md:mt-12">
                    <div class="rounded-3xl bg-white shadow-lg">
                        <div class="px-4 py-6 sm:px-8 sm:py-10">
                            <div class="flow-root">
                                <ul class="-my-8">
                                    <li
                                        class="flex items-center flex-col space-y-3 py-6 text-left sm:flex-row sm:space-x-5 sm:space-y-0">
                                        <div class="shrink-0 relative">
                                            <img class="h-24 w-24 max-w-full rounded-lg object-cover"
                                                src="../assets/money-dynamic-color.svg" alt="" />
                                        </div>

                                        <div class="relative flex flex-1 flex-col justify-between">
                                            <div class="sm:col-gap-5 sm:grid sm:grid-cols-2">
                                                <div class="pr-8 sm:pr-5">
                                                    <p class="text-base font-semibold text-gray-900">{{ CheckoutData?.description }}</p>
                                                    #{{ CheckoutData?.id }}                                                 
                                                </div>

                                                <div
                                                    class="mt-4 flex items-end justify-between sm:mt-0 sm:items-start sm:justify-end">
                                                    <p
                                                        class="shrink-0 w-20 text-base font-semibold text-gray-900 sm:order-2 sm:ml-8 sm:text-right">
                                                        Rp {{ CheckoutData?.nominal }}</p>
                                                </div>
                                            </div>
                                        </div>
                                    </li>                                    
                                </ul>
                            </div>
                            <div class="mt-6 flex items-center justify-between">
                                <p class="text-sm font-medium text-gray-900">Total</p>
                                <p class="text-2xl font-semibold text-gray-900"><span
                                        class="text-xs font-normal text-gray-400">Rp </span> Rp {{ CheckoutData?.nominal }}</p>
                            </div>

                            <div class="mt-6 text-center">
                                <div class="flex justify-center space-x-4">
                                    <div class="w-1/2">
                                        <button id="cancel-button" type="button"
                                            class="group inline-flex items-center justify-center rounded-md bg-red-500 w-full mt-3 px-6 py-4 text-lg font-semibold text-white transition-all duration-200 ease-in-out focus:shadow hover:bg-red-800 rounded-xl">
                                            <router-link to="/homepage" class="flex items-center justify-center h-full">
                                                Cancel
                                            </router-link>
                                        </button>
                                    </div>

                                    <div class="w-1/2">
                                        <button id="pay-button" type="button"
                                            class="group inline-flex items-center justify-center rounded-md bg-orange-500 w-full mt-3 px-6 py-4 text-lg font-semibold text-white transition-all duration-200 ease-in-out focus:shadow hover:bg-gray-800 rounded-xl"
                                            @click="handleCheckout">
                                            Checkout
                                            <svg xmlns="http://www.w3.org/2000/svg"
                                                class="group-hover:ml-8 ml-4 h-6 w-6 transition-all" fill="none" viewBox="0 0 24 24"
                                                stroke="currentColor" stroke-width="2">
                                                <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                                            </svg>
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <div id="snap-container"></div>
    </body>
</template>

<script setup>
import Homepage from '@/components/Homepage.vue'
import router from '@/router';
import axios from 'axios';
import { ref } from 'vue';

const LoanData = ref(null);
const PaymentLoan = ref(null);
const CheckoutData = ref(null);

// Fungsi untuk memanggil API dan mengisi data CheckoutData
async function callingAPILoan() {
  try {
    const authToken = localStorage.getItem('login_token');
    if (!authToken) {
      router.push({ path: '/' });
      return;
    }
    
    const responseData = await axios.get('http://localhost:8000/api/checkoutData', {
      headers: {
        Authorization: `Bearer ${authToken}`,
      },
    });
    
    CheckoutData.value = responseData.data.Data.Data;
  } catch (error) {
    console.error(error);
    router.push({ path: '/homepage' });
  }
}

callingAPILoan();

// Fungsi untuk menangani pembayaran saat tombol "Checkout" diklik
const handleCheckout = () => {
  if (CheckoutData.value) {
    const transactionToken = CheckoutData.value.snap_token;
    window.snap.pay(transactionToken, {
      onSuccess: function(result){
        window.location.href = '/invoice'                
      },
      onPending: function(result){
        alert("Waiting for payment!");
        console.log(result);
      },
      onError: function(result){
        alert("Payment failed!");
        console.log(result);
      },
      onClose: function(){
        alert("You closed the popup without finishing the payment");
      }      
    });
  }
};
</script>

<script>
// Tambahkan skrip Midtrans di sini
const midtransScript = document.createElement('script');
midtransScript.type = 'text/javascript';
midtransScript.src = 'https://app.sandbox.midtrans.com/snap/snap.js';
midtransScript.setAttribute('data-client-key', 'SB-Mid-client-T9jrTX0BmSV206rm');
document.head.appendChild(midtransScript);
</script>
