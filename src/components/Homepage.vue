<template>
    <!DOCTYPE html>

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Login Page</title>

        <link rel="stylesheet"
            href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    </head>

    <body>
        <div class="main">
            <!-- <div class="logo"></div> -->

            <div class="credentials">
                <div class="card">
                    <v-card :elevation="0" max-width="350" class="">
                        <v-container>
                            <div class="logout">
                                <form class="logout">
                                    <v-btn @click="logout()" class="bg-red-darken-4" variant="tonal" type="button"> Logout </v-btn>
                                </form>
                            <div class="profile-user pt-2 pb-2">
                                <v-card class="mx-auto" max-width="350" variant="tonal">
                                    <v-card-item class="bg-grey-lighten-5">
                                        <div>
                                            <div class=" d-flex align-center justify-space-between text-overline mb-1">
                                                Profil

                                            </div>
                                            <div class="text-h6 mb-1">{{ UserData?.name }}</div>
                                            <div class="text-caption">{{ UserData?.email }}</div>
                                            <div class="text-caption">{{ UserData?.phone_number }}</div>
                                        </div>
                                    </v-card-item>
                                </v-card>
                            </div>
                                
                            </div>

                            <div class="tabungan-wajib" v-for="UserSavings in SavingsData" :key="UserSavings.id">
                                <v-card class="mx-auto pb-2" max-width="350" variant="tonal">
                                    <v-card-item class="bg-teal-lighten-3">
                                        <div>
                                            <div class="text-overline mb-1">Tabungan Wajib</div>
                                            <div class="text-h6 mb-1">RP {{ UserSavings.nominal }}</div>                                            
                                        </div>
                                    </v-card-item>
                                    <v-card-actions class="bg-teal-lighten-3">
                                            <form class="FormSaving">
                                                <v-btn variant="tonal" @click="PostPaymentMoneyLoan(UserData?.id, UserSavings.id, 'Mandatory Savings',UserSavings.nominal)" type="button">Bayar</v-btn>
                                            </form>                                                                                        
                                    </v-card-actions>                                    
                                </v-card>
                            </div>

                            <div class="pinjaman-uang" v-for="UserMoneyLoan in MoneyLoanData" :key="UserMoneyLoan.id">
                                <v-card class="mx-auto pb-2 " max-width="350" variant="tonal">
                                    <v-card-item class="bg-light-green-lighten-1">
                                        <div>
                                            <div class="text-overline mb-1">Pinjaman Uang</div>
                                            <div id="month" class="text-body-1">Bulan ke-{{ UserMoneyLoan.month }}</div>
                                            <div class="text-body-1">Status Pembayaran: {{ UserMoneyLoan.status }}</div>
                                            <div id="amount" class="text-body-2">Nominal: Rp {{ UserMoneyLoan.installment_amount }}</div>                                                                                                                       
                                        </div>
                                    </v-card-item>
                                    <v-card-actions class="bg-light-green-lighten-1">
                                        <form class="FormMoneyLoan">
                                                <v-btn variant="tonal" @click="PostPaymentMoneyLoan(UserData?.id, UserMoneyLoan.id, 'Loan Fund',UserMoneyLoan.installment_amount)" type="button">Bayar</v-btn>
                                            </form>                                                                                        
                                    </v-card-actions>
                                </v-card>
                            </div>

                            <!-- <div class="pinjaman-uang">
                                <v-card class="mx-auto pb-2 " max-width="350" variant="tonal">
                                    <v-card-item class="bg-light-red-lighten-1">
                                        <div>
                                            <div class="text-caption">looping data</div>

                                            <div v-for=" userloan in MoneyLoanData" :key="userloan.id">
                                                <div class="text-caption">{{ userloan.month }}</div>
                                                <div class="text-caption">{{ userloan.status }}</div>
                                            </div>

                                        </div>
                                    </v-card-item>

                                </v-card>
                            </div> -->

                            <div class="pinjaman-barang" v-for="UserGoodsLoan in GoodsLoanData" :key="UserGoodsLoan.id">
                                <v-card class="mx-auto" max-width="350" variant="tonal">
                                    <v-card-item class="bg-lime-lighten-1">
                                        <div>
                                            <div class="text-overline mb-1">Pinjaman Barang</div>
                                            <div class="text-body-1">Bulan ke-{{ UserGoodsLoan.month }}</div>
                                            <div class="text-body-1">Status Pembayaran: {{ UserGoodsLoan.status }}</div>
                                            <div class="text-body-2">Nominal: Rp {{ UserGoodsLoan.installment_amount }}                                            
                                            </div>                                            
                                        </div>
                                    </v-card-item>

                                    <v-card-actions class="bg-lime-lighten-1">
                                        <form class="FormGoodsLoan">
                                                <v-btn variant="tonal" @click="PostPaymentMoneyLoan(UserData?.id, UserGoodsLoan.id, 'Goods Loan',UserGoodsLoan.installment_amount)" type="button">Bayar</v-btn>
                                            </form>                                        
                                    </v-card-actions>
                                </v-card>
                            </div>

                        </v-container>
                    </v-card>
                </div>
            </div>
        </div>
    </body>
</template>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    --body-background-color-one: #17ffc6;
    --body-background-color-two: #086070;

    --main-background-color: #fff;

    --submit-background-color-one: #4EFA99;
    --submit-background-color-two: #3ED656;
    --submit-background-color-three: #68ED51;

    --submit-box-shadow: #b1b1b1;
}

body {
    min-height: 100vh;
    display: flex;
    align-items: center;
    /* color: #03a1fc; */
    background-image: linear-gradient(to right, var(--body-background-color-one), var(--body-background-color-two));
    justify-content: center;
}

.FormMoneyLoan {
    
}

.FormMoneyLoan #SubmitMoneyLoan {
    display: block !important;
}

.main {
    /* width: 450px;
    padding: 60px 35px 35px 35px; */
    border-radius: 20px;
    transition: all 1s ease;
    background-color: var(--main-background-color);
    font-family: sans-serif;
    font-weight: 700;
    overflow: auto;
}

.credentials {
    width: 100%;
    padding: 2px 5px 0 5px;
}

@media (max-width: 540px) {
    .main {
        width: 100%;
        min-height: 100%;
        border-radius: 0;
    }

    body {
        height: 100vh;
    }

    .credentials {
        display: flex;
        justify-content: center;
    }
}

@media (max-width: 768px) {
    body {
        height: auto;
    }
}
</style>

<script>
import axios from 'axios';

export default {
    data: () => ({
        UserData: null,
        MoneyLoanData: null,
        GoodsLoanData: null,
        SavingsData: null,
        async callingAPIProfile() {
            try {
                // Retrieve the authentication token from localStorage
                const authToken = localStorage.getItem('login_token');
                if (!authToken) {
                    // Handle the case when the user is not logged in or token is missing
                    router.push({ path: '/' });
                    return;
                }
                // Make the API request to fetch user data
                const response = await axios.get('http://localhost:8000/api/profile', {
                    headers: {
                        Authorization: `Bearer ${authToken}`,
                    },
                });
                // console.log(response.data.data.user);
                this.UserData = response.data.Data.User;
                // Handle the response and store the user data
            } catch (error) {
                // Handle errors, e.g., token expired, server error, etc.
                console.error(error);
            }
        },
        async CallingAPILoan() {
            try {
                // Retrieve the authentication token from localStorage
                const authToken = localStorage.getItem('login_token');               
                // Make the API request to fetch user data
                var Response = await axios.get('http://localhost:8000/api/user', {
                    headers: {
                        Authorization: `Bearer ${authToken}`,
                    },
                });
                // Handle the response and store the user data
                this.MoneyLoanData = Response.data.Data.LoanFundsBills;
                this.GoodsLoanData = Response.data.Data.GoodsLoanBills;
                this.SavingsData = Response.data.Data.savings;
                // console.log(Response.data.Data.Savings[0].nominal);
                // console.log(Response.data.Data.savings[0].nominal);
            } catch (error) {
                // Handle errors, e.g., token expired, server error, etc.
                console.error(error);
                router.push({ path: '/' });
            }
        },
        PostPaymentMoneyLoan(user_id, bills_id, description, installment_amount) {
            const authToken = localStorage.getItem('login_token');
            const paymentData = {
                user_id: user_id,
                bills_id: bills_id,
                description: description,
                nominal: installment_amount,
                status: 'Unpaid'
            };

            axios.post('http://localhost:8000/api/payments', paymentData, {
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${authToken}`
                }
            })
            .then(response => {
                console.log(response.data);
                router.push({ path: '/checkoutmoneyloan' });
            })            
            .catch(error => {
                console.error('Payment API error:', error.response);
            });
        },
        logout(){
            const authToken = localStorage.getItem('login_token');
            axios.post('http://localhost:8000/api/logout', null,{
                headers: {                                    
                    'Authorization': `Bearer ${authToken}`
                }
            })
            .then(response => {
                console.log("API". authToken);
                console.log(response.data);
                localStorage.removeItem('login_token');
                router.push({ path: '/' });
            })            
            .catch(error => {
                console.error('Logout API error:', error.response);
            });
        }
    }),
    mounted() {
        // Call the method to fetch user data after successful login
        this.callingAPIProfile();
        this.CallingAPILoan();
    },
    methods: {
    }
}
</script>
<script setup>
import router from '@/router';
</script>
