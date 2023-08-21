<template>
    <div class="bg-white border rounded-lg shadow-lg px-6 py-8 max-w-md mx-auto mt-8">
        <h1 class="font-bold text-2xl my-4 text-center text-blue-600">Baitul Maal Wat Tamwil</h1>
        <hr class="mb-2">
        <div class="flex justify-between mb-6">
            <h1 class="text-lg font-bold">Invoice</h1>
            <div class="text-gray-700">
                <div>Payment Id: <!-- {{ panggil API payment_id }} -->#{{ CheckoutData?.id }}</div>
                <div>Bills Id<!-- {{ panggil API bills_id }} -->: #{{ CheckoutData?.bills_id }}</div>
            </div>
        </div>
        <table class="w-full mb-8">
            <thead>
                <tr>
                    <th class="text-left font-bold text-gray-700">Status Pembayaran</th>
                    <th class="text-right font-bold text-gray-700"><!--Panggil API Status-->{{ CheckoutData?.status }}</th>
                </tr>
            </thead>
        </table>        
        <table class="w-full mb-8">
            <thead>
                <tr>
                    <th class="text-left font-bold text-gray-700">Deskripsi</th>
                    <th class="text-right font-bold text-gray-700">Jumlah</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="text-left text-gray-700"><!-- {{ panggil API Deskripsi }} -->{{ CheckoutData?.description }}</td>
                    <td class="text-right text-gray-700"><!-- {{ panggil API nominal }} -->  Rp {{ CheckoutData?.nominal }}</td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <td class="text-left font-bold text-gray-700">Nominal</td>
                    <td class="text-right font-bold text-gray-700"><!-- {{ panggil API nominal }} -->  Rp {{ CheckoutData?.nominal }}</td>
                </tr>
            </tfoot>
        </table>
        <div class="text-gray-700 mb-2">Terima Kasih!</div>
      <v-btn class="bg-blue-darken-3" variant="tonal" type="button"><router-link to="/homepage">Kembali</router-link></v-btn>
        <br>
    </div>
</template>

<script setup>
import router from '@/router';
import axios from 'axios';
import { ref } from 'vue';

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
  }
}

callingAPILoan();
</script>
