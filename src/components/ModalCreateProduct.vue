<template>
    <div  class="text-right">
        <v-dialog v-model="dialog" width="500px">

            <template v-slot:activator="{ on, attrs }">
                <v-btn color="primary" dark class="mb-2" v-bind="attrs" v-on="on" >Produk Baru</v-btn>
            </template>

            <v-card>
                <v-card-title>
                    <span class="headline">Produk Baru</span>
                </v-card-title>

                <v-card-text>
                    <v-container>
                        <v-row>
                            <v-col cols="12" sm="12">
                                <v-text-field label="Name Produk" :value="defaultItem"></v-text-field>
                            </v-col>

                            <v-col cols="12" sm="12">
                                <v-text-field label="Jumlah"  :value="defaultItem"></v-text-field>
                            </v-col>

                            <v-col cols="12" sm="12">
                                <v-text-field label="Harga"  :value="defaultItem"></v-text-field>
                            </v-col>
                        </v-row>
                    </v-container>
                </v-card-text>

                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="dialog = !dialog">Save</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
  export default {
    props : { defaultItem },
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>

