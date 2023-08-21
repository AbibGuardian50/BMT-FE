<template>
    <head>
        <link rel="stylesheet"
            href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    </head>

    <body>
        <div class="main">
            <div class="logo"></div>
            <div class="title">Masukkan Kode Anggota</div>

            <v-card class="mx-auto pa-2" max-width="450">
                <v-list>
                    <v-list-subheader>REPORTS</v-list-subheader>

                    <v-list-item v-for="(item, i) in items" :key="i" :value="item" color="primary" rounded="xl">
                        <template v-slot:prepend>
                            <v-icon :icon="item.icon"></v-icon>
                        </template>

                        <v-list-item-title v-text="item.text"></v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-card>

        </div>
    </body>
</template>

<script>
export default {
    data: () => ({
        items: [
            { text: 'Saldo', icon: 'mdi-account-cash' },
            { text: 'Tagihan Pinjaman Uang', icon: 'mdi-cash-multiple' },
            { text: 'Tagihan Pinjaman Barang', icon: 'mdi-basket' },
        ],
    }),
}
</script>