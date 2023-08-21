<template>
    <v-container>
        <div id="card-balance" class="v-application__wrap">
            <v-card title="Tabungan Wajib" :subtitle='UserData?.mandatory_savings' variant="tonal">
                <!--untuk show balance,nanti nya pada subtitle menggunakan:subtitle dengan ternary,jika benar maka API dipanggil dan jika salah maka tetap sama-->
                <v-card-actions>
                    <v-dialog v-model="dialog" persistent width="768">
                        <template v-slot:activator="{ props }">
                            <v-btn class="text-red-500" color="#5865f2" variant="flat" v-bind="props"> Tampilkan Saldo
                            </v-btn>
                        </template>
                        <v-card>
                            <v-card-title>
                                <span class="text-h5">Masukkan Pin Anggota</span>
                            </v-card-title>
                            <v-card-text>
                                <v-container>
                                    <v-row>
                                        <v-col cols="12">
                                            <v-text-field label="Pin*" type="password" required></v-text-field>
                                        </v-col>
                                    </v-row>
                                </v-container>
                                <small>*indicates required field</small>
                            </v-card-text>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn color="blue-darken-1" variant="text" @click="dialog = false">
                                    Close
                                </v-btn>
                                <v-btn color="blue-darken-1" variant="text" @click="dialog = false">
                                    Save
                                </v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-dialog>


                </v-card-actions>
            </v-card>
        </div>
    </v-container>
</template>

<style scoped>
.v-application__wrap {
    min-height: 0vh !important;
    /* max-width: 72; */
}
</style>

<script>
import axios from 'axios';
export default {
    data: () => ({
        UserData: null,
        dialog: false,
        async callingApiName() {
            try {
                // Retrieve the authentication token from localStorage
                const authToken = localStorage.getItem('login_token');
                if (!authToken) {
                    // Handle the case when the user is not logged in or token is missing
                    // Redirect to login page or show an error message, etc.
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
    }),

    mounted() {
        // Call the method to fetch user data after successful login
        this.callingApiName();
    },


    methods: {
        showbalance() {
            let text = document.getElementById('card-balance').innerHTML;
            document.getElementById('card-balance').innerHTML = text.replace("Rp ******", "Rp 250.000");
        }
    }

}
</script>