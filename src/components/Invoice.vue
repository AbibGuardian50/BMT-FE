<template>
    <div class="bg-white border rounded-lg shadow-lg px-6 py-8 max-w-md mx-auto mt-8">
        <h1 class="font-bold text-2xl my-4 text-center text-blue-600">Baitul Maal Wat Tamwil</h1>
        <hr class="mb-2">
        <div class="flex justify-between mb-6">
            <h1 class="text-lg font-bold">Invoice</h1>
            <div class="text-gray-700">
                <div>Payment Id: <!-- {{ panggil API payment_id }} -->243545</div>
                <div>Bills Id<!-- {{ panggil API bills_id }} -->: INV12345</div>
            </div>
        </div>
        <table class="w-full mb-8">
            <thead>
                <tr>
                    <th class="text-left font-bold text-gray-700">Status Pembayaran</th>
                    <th class="text-right font-bold text-gray-700"><!--Panggil API Status-->Telah Dibayar</th>
                </tr>
            </thead>
        </table>
        <!-- <div class="mb-8">
            <h2 class="text-lg font-bold mb-4">Status Pembayaran</h2>
            <div class="text-gray-700 mb-2">John Doe</div>
            <div class="text-gray-700 mb-2">123 Main St.</div>
            <div class="text-gray-700 mb-2">Anytown, USA 12345</div>
            <div class="text-gray-700">johndoe@example.com</div>
        </div> -->
        <table class="w-full mb-8">
            <thead>
                <tr>
                    <th class="text-left font-bold text-gray-700">Deskripsi</th>
                    <th class="text-right font-bold text-gray-700">Jumlah</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="text-left text-gray-700"><!-- {{ panggil API Deskripsi }} -->Pinjaman Uang</td>
                    <td class="text-right text-gray-700"><!-- {{ panggil API nominal }} -->  Rp 125.000</td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <td class="text-left font-bold text-gray-700">Nominal</td>
                    <td class="text-right font-bold text-gray-700"><!-- {{ panggil API nominal }} -->  Rp 125.000</td>
                </tr>
            </tfoot>
        </table>
        <div class="text-gray-700 mb-2">Terima Kasih!</div>
    </div>
</template>