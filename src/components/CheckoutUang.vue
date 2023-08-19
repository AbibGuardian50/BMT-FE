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
                                                    <p class="text-base font-semibold text-gray-900">Pinjaman Uang</p>
                                                    <!-- <p class="mx-0 mt-1 mb-0 text-sm text-gray-400">36EU - 4US</p> -->
                                                </div>

                                                <div
                                                    class="mt-4 flex items-end justify-between sm:mt-0 sm:items-start sm:justify-end">
                                                    <p
                                                        class="shrink-0 w-20 text-base font-semibold text-gray-900 sm:order-2 sm:ml-8 sm:text-right">
                                                        Rp {{ LoanData?.[0].installment_amount }}</p>
                                                </div>
                                            </div>

                                            <!-- <div class="absolute top-0 right-0 flex sm:bottom-0 sm:top-auto">
                                                <button type="button"
                                                    class="flex rounded p-2 text-center text-gray-500 transition-all duration-200 ease-in-out focus:shadow hover:text-gray-900">
                                                    <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none"
                                                        viewBox="0 0 24 24" stroke="currentColor">
                                                        <path stroke-linecap="round" stroke-linejoin="round"
                                                            stroke-width="2" d="M6 18L18 6M6 6l12 12" class=""></path>
                                                    </svg>
                                                </button>
                                            </div> -->
                                        </div>
                                    </li>
                                    <!-- <li
                                        class="flex flex-col space-y-3 py-6 text-left sm:flex-row sm:space-x-5 sm:space-y-0">
                                        <div class="shrink-0 relative">
                                            <span
                                                class="absolute top-1 left-1 flex h-6 w-6 items-center justify-center rounded-full border bg-white text-sm font-medium text-gray-500 shadow sm:-top-2 sm:-right-2">1</span>
                                            <img class="h-24 w-24 max-w-full rounded-lg object-cover"
                                                src="https://images.unsplash.com/photo-1600185365483-26d7a4cc7519?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8OHx8c25lYWtlcnxlbnwwfHwwfHw%3D&auto=format&fit=crop&w=150&q=60"
                                                alt="" />
                                        </div>

                                        <div class="relative flex flex-1 flex-col justify-between">
                                            <div class="sm:col-gap-5 sm:grid sm:grid-cols-2">
                                                <div class="pr-8 sm:pr-5">
                                                    <p class="text-base font-semibold text-gray-900">Nike Air Max 2019</p>
                                                    <p class="mx-0 mt-1 mb-0 text-sm text-gray-400">36EU - 4US</p>
                                                </div>

                                                <div
                                                    class="mt-4 flex items-end justify-between sm:mt-0 sm:items-start sm:justify-end">
                                                    <p
                                                        class="shrink-0 w-20 text-base font-semibold text-gray-900 sm:order-2 sm:ml-8 sm:text-right">
                                                        $1259.00</p>
                                                </div>
                                            </div>

                                            <div class="absolute top-0 right-0 flex sm:bottom-0 sm:top-auto">
                                                <button type="button"
                                                    class="flex rounded p-2 text-center text-gray-500 transition-all duration-200 ease-in-out focus:shadow hover:text-gray-900">
                                                    <svg class="block h-5 w-5" xmlns="http://www.w3.org/2000/svg"
                                                        fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                                        <path stroke-linecap="round" stroke-linejoin="round"
                                                            stroke-width="2" d="M6 18L18 6M6 6l12 12" class=""></path>
                                                    </svg>
                                                </button>
                                            </div>
                                        </div>
                                    </li> -->
                                </ul>
                            </div>

                            <!-- <hr class="mx-0 mt-6 mb-0 h-0 border-r-0 border-b-0 border-l-0 border-t border-solid border-gray-300" /> -->

                            <!-- <div class="mt-6 space-y-3 border-t border-b py-8">
                                <div class="flex items-center justify-between">
                                    <p class="text-gray-400">Subtotal</p>
                                    <p class="text-lg font-semibold text-gray-900">Rp 450.000</p>
                                </div>
                                <div class="flex items-center justify-between">
                                    <p class="text-gray-400">Shipping</p>
                                    <p class="text-lg font-semibold text-gray-900">$8.00</p>
                                </div>
                            </div> -->
                            <div class="mt-6 flex items-center justify-between">
                                <p class="text-sm font-medium text-gray-900">Total</p>
                                <p class="text-2xl font-semibold text-gray-900"><span
                                        class="text-xs font-normal text-gray-400">Rp </span> {{
                                            LoanData?.[0].installment_amount }}</p>
                            </div>

                            <div class="mt-6 text-center">
                                <button id="pay-button" type="button"
                                    class="group inline-flex w-full items-center justify-center rounded-md bg-orange-500 px-6 py-4 text-lg font-semibold text-white transition-all duration-200 ease-in-out focus:shadow hover:bg-gray-800 rounded-xl">
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
        </section>

        <div id="snap-container"></div>
    </body>
</template>


<script data-client-key="SET_YOUR_CLIENT_KEY_HERE">
import axios from 'axios';
export default {
    // metaInfo: {
    //     script: [
    //         { src: "https://app.stg.midtrans.com/snap/snap.js", async: true, defer: true },

    //     ]
    // },
    // SNAP IS NOT DEFINED!!!!!
    // setup() {
    //     const recaptchaScript = document.createElement("script");
    //     recaptchaScript.setAttribute(
    //         "src",
    //         "https://app.stg.midtrans.com/snap/snap.js"
    //     );
    //     document.head.appendChild(recaptchaScript);
    // },
    data: () => ({
        LoanData: null,
        async callingAPILoan() {
            try {
                // Retrieve the authentication token from localStorage
                const authToken = localStorage.getItem('login_token');
                if (!authToken) {
                    // Handle the case when the user is not logged in or token is missing
                    router.push({ path: '/' });
                    return;
                }
                // Make the API request to fetch user data
                const response = await axios.get('http://localhost:8000/api/user', {
                    headers: {
                        Authorization: `Bearer ${authToken}`,
                    },
                });
                // console.log(response.data.data.user);
                this.LoanData = response.data.Data.LoanFundsBills;
                console.log(response.data.Data.LoanFundsBills);
                // Handle the response and store the user data
            } catch (error) {
                // Handle errors, e.g., token expired, server error, etc.
                console.error(error);
            }
        },
    }),
    mounted() {
        this.callingAPILoan();
        // let Script = document.createElement("script");
        // Script.setAttribute("src", "https://app.stg.midtrans.com/snap/snap.js");
        // document.head.appendChild(Script);
    }
};
// snap.pay('3c24070e-1bac-4b43-9de0-cd57e34622cf', {
//     onSuccess: function (result) { console.log('success'); console.log(result); },
//     onPending: function (result) { console.log('pending'); console.log(result); },
//     onError: function (result) { console.log('error'); console.log(result); },
//     onClose: function () { console.log('customer closed the popup without finishing the payment'); }
// })
// function ajaxGetToken(transactionData, callback) {
//     var snapToken;
//     // Request get token to your server & save result to snapToken variable

//     if (snapToken) {
//         callback(null, snapToken);
//     } else {
//         callback(new Error('Failed to fetch snap token'), null);
//     }
// }

// payButton.onclick(function () {
//     snap.show();
//     ajaxGetToken(transactionData, function (error, snapToken) {
//         if (error) {
//             snap.hide();
//         } else {
//             snap.pay(snapToken);
//         }
//     });
// });

// var payButton = document.getElementById('pay-button');
// payButton.addEventListener('click', function () {
//     // Trigger snap popup. @TODO: Replace TRANSACTION_TOKEN_HERE with your transaction token.
//     // Also, use the embedId that you defined in the div above, here.
//     window.snap.embed('YOUR_SNAP_TOKEN', {
//         embedId: 'snap-container'
//     });
// });
</script>