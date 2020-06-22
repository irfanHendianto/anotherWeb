<template>
  <div class="home">
    <v-subheader>Home</v-subheader>
    <v-container>
        <v-layout row wrap justify-end class="ma-auto">

          <v-flex md1 xs12>
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
                                        <v-text-field label="Name Produk" v-model="editedItem.nama_product"></v-text-field>
                                    </v-col>

                                    <v-col cols="12" sm="12">
                                        <v-text-field label="Jumlah"  v-model="editedItem.jumlah"></v-text-field>
                                    </v-col>

                                    <v-col cols="12" sm="12">
                                        <v-text-field label="Harga"  v-model="editedItem.Harga"></v-text-field>
                                    </v-col>
                                </v-row>
                            </v-container>
                        </v-card-text>

                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="blue darken-1" text @click="close">Cancel</v-btn>
                            <v-btn color="blue darken-1" text @click="save">Save</v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </div>
          </v-flex>

          <v-flex lg1 md2 xs12 style="margin-left: 3%;">
            <div class="text-right">
              <v-dialog
                v-model="file"
                width="500"
              >
                <template v-slot:activator="{ on, attrs }">
                    
                  <v-btn
                    color="primary"
                    dark
                    v-bind="attrs"
                    v-on="on"
                    class="pop_up"
                  >
                    Add
                  </v-btn>
                </template>

                <v-card>
                  <v-card-title
                    class="headline grey lighten-2"
                    primary-title
                  >
                    Upload File
                  </v-card-title>

                  <v-card-text>
                      <v-file-input multiple label="File input" v-model="fileUpload" ></v-file-input>
                  </v-card-text>

                  <v-divider></v-divider>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                      color="primary"
                      text
                      @click="upload"
                    >
                      Submit
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </div>
          </v-flex>

        </v-layout>
        <v-card>
          <v-card-title>
            Produk
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
            :headers="headers"
            :items="product"
            :search="search"
            :items-per-page="5"
          >
            <template v-slot:item.actions="{ item }">
              <v-icon
                small
                class="mr-2"
                @click="editItem(item)"
              >
                mdi-pencil
              </v-icon>
              <v-icon
                small
                @click="deleteItem(item)"
              >
                mdi-delete
              </v-icon>
            </template>
          
          </v-data-table>
        </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
// import Popup from '../components/Popup'
export default {
  name: 'Home',
  // components:{Popup},
  data(){
    return {
        search: '',
        dialog: false,
        file: false,
        fileUpload:[],
        headers: [
          { text: 'Nama Produk', value: 'nama_product' },
          { text: 'Jumlah', value: 'jumlah' },
          { text: 'Harga', value: 'Harga' },
          { text: 'Actions', value: 'actions', sortable: false },
        ],
        product: [],
        editedIndex: -1,
        editedItem: {
          nama_product: '',
          jumlah: '0',
          Harga: '0',
        },
        defaultItem: {
          nama_product: '',
          jumlah: '0',
          Harga: '0',
        },
      }
  },
  methods:{
    fetchProduct(){
      axios.get('http://localhost:3000/list').then(response=>{
        this.product = response.data.data;
        console.log(response.data.data);
      })
    },
    editItem (item) {
      this.editedIndex = this.product.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },
    deleteItem (item) {
      const index = this.product.indexOf(item);
      confirm('Are you sure you want to delete this item?') && this.product.splice(index, 1);
      axios.delete('http://localhost:3000/product/'+ item.No).then(responsen=>{
        console.log(responsen);
      });
    },
    close () {
      this.dialog = false
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      })
    },
    save () {
      if (this.editedIndex > -1) {
        console.log(this.editedItem.No);
          axios.put('http://localhost:3000/editProduct/'+this.editedItem.No ,{nama_product: this.editedItem.nama_product, jumlah: this.editedItem.jumlah, Harga: this.editedItem.Harga}).then(response =>{
          console.log(response);
        });
        Object.assign(this.product[this.editedIndex], this.editedItem)

      } else {
        axios.post('http://localhost:3000/addProduct',{nama_product: this.editedItem.nama_product, jumlah: this.editedItem.jumlah, Harga: this.editedItem.Harga}).then(response =>{
          console.log(response);
        });
        this.product.push(this.editedItem)
      }
      this.close()
    },
    upload(){
       this.file = false
       const fd = new FormData();
       fd.append('files', this.fileUpload[0])
       axios.post('http://localhost:3000/upload',fd).then(response =>{
         for(let i = 0 ; i< response.data.data.length ; i++) {
           this.product.push(response.data.data[i]);
          }
       });
       this.fileUpload = [];
    },
  },
  mounted(){
    this.fetchProduct();
  }
 
}
</script>
