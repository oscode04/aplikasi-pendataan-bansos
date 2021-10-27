<template>
  <v-app>
    <v-main class="background">

    <header-kom></header-kom>
      
    <!-- error message -->
    <v-container v-if="errors.length != ''">
      <v-card
      class="mx-auto"
      max-width="80%"
      >
        <v-card-text>
          <p>
            <b>TOLONG ISI DATA DENGAN BENAR DAN LENGKAP</b>
            <ul>
              <li v-for="error in errors" :key="error">{{error}}</li>
            </ul>
          </p>
        </v-card-text>
      </v-card>
    </v-container>
    <!-- field nama -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Nama
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="name"
                  :rules="nameRules"
                  label="Masukan nama disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>

    <!-- field nik -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              NIK
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="nik"
                  :rules="nikRules"
                  label="Masukan nomor NIK disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>

    <!-- field nomor kk -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Nomor KK
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="kk"
                  :rules="kkRules"
                  label="Masukan nomor KK disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>
    
    <!-- upload KTP -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Masukan foto KTP
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
                
              >
             <v-file-input
             v-model="uploadKtp"
                :rules="rules"
                label="File input"
                filled
                type="file"
                ref="ktp"
                name="ktp"
                prepend-icon="mdi-camera"
              ></v-file-input>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>

    <!-- Upload KK -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Masukan foto KK
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
             <v-file-input
             v-model="uploadKk"
                :rules="rules"
                label="File input"
                filled
                prepend-icon="mdi-camera"
              ></v-file-input>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>

    
    <!-- field Umur -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Umur
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="umur"
                  :rules="umurRules"
                  label="Masukan umur disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>

    </v-container>

    <!-- option jenis kelamin -->
     <v-container>

       <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Jenis kelamin
            </p>
            <!-- <p>
              Pilih jenis kelamin
            </p> -->
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container class="mt-n6">
            <v-row>
              <v-col
                md="12"
              >
              <h3>{{ jenisKelamin || 'null' }}</h3>
                <v-radio-group
                  v-model="jenisKelamin"
                  mandatory
                >
                  <v-radio
                    label="Laki-laki"
                    value="Laki-laki"
                  ></v-radio>
                  <v-radio
                    label="Perempuan"
                    value="Perempuan"
                  ></v-radio>
                </v-radio-group>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>

    </v-container>

    <!-- field untuk alamat -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Alamat
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="alamat"
                  :rules="alamatRules"
                  label="Masukan alamat disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-card-text>
              </v-card-text>
                <v-col md="6" cols="12">
                  <div class="mt-n11" >
                    <p class="mb-n4">
                      RT
                    </p>
                    <v-select
                      v-model="alamatrt"
                      :items="rt"
                      :menu-props="{ top: true, offsetY: true }"
                      required
                    ></v-select>
                  </div>
                </v-col>
                <v-col md="6" cols="12">
                  <div class="mt-n11">
                      <p class="mb-n4">
                        RW
                      </p>
                      <v-select
                        v-model="alamatrw"
                        :items="rw"
                        :menu-props="{ top: true, offsetY: true }"
                        required
                      ></v-select>
                  </div>
                </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>

    <!-- penghasilan sebelum pandemi -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Penghasilan sebelum pandemi
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="penghasilansbl"
                  :rules="penghasilanRules"
                  label="Masukan pengahasilan disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>

    </v-container>

    <!-- penghasilan sesudah pandemi -->
    <v-container>
      <v-card
        class="mx-auto"
        max-width="80%"
      >
          <v-card-text>
            <p class="text-h4 text--primary">
              Penghasilan sesudah pandemi
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
            <v-row>
              <v-col
                md="12"
              >
              <v-text-field
                  class="mt-n6"
                  v-model="penghasilansudah"
                  :rules="penghasilanRules"
                  label="Masukan pengahasilan disini"
                  required
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-container>
    
    <v-container>
      <v-card
      class="mx-auto"
      max-width="80%"
      min-height="50px"
      >
        <v-checkbox
        v-model="checkbox"
        color="success"
        class="ml-2"
      >
        <template v-slot:label>
          <div>
            <p class="mb-n1 text--primary text-align">Saya menyatakan bahwa data yang diisikan adalah benar dan siap mempertanggungjawabkan apabila ditemukan ketidaksesuaian dalam data tersebut.</p>
          </div>
        </template>
      </v-checkbox>
      </v-card>
    </v-container>

    <!-- tombol submit -->
    <v-container>
      <div class="text-center mb-5">
          <v-btn rounded color="primary accent-3" dark @click="requaredValidation"  width="80%" height="50" > <h1>Submit</h1> </v-btn>
      </div>
    </v-container>
    
    </v-main>
  </v-app>
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
   data () {
     return {
      valid: false,
      name: '',
      nik: '',
      kk: '',
      uploadKtp:null,
      uploadKk:null,
      umur:'',
      alamat:'',
      alamatrt:'',
      alamatrw:'',
      jenisKelamin: null,
      penghasilansudah:'',
      penghasilansbl:'',
      checkbox: false,
      nameRules: [
        v => !!v || 'nama wajib di tulis',
      ],
      nikRules: [
        v => !!v || 'NIK wajib di isi',
      ],
      kkRules: [
        v => !!v || 'KK wajib di isi',
      ],
      umurRules: [
        v => !!v || 'umur wajib di isi',
      ],
      alamatRules: [
        v => !!v || 'alamat wajib di isi',
        v => v.length <= 255 || 'Alamat harus kurang dari 255 huruf',
      ],
      penghasilanRules: [
        v => !!v || 'penghasilan wajib di isi',
      ],
      rules: [
        value => !value || value.size < 2000000 || 'ukuran foto tidak boleh lebih dari 2 MB!',
      ],
      rt: this.lopingRt(),
      rw: this.lopingRw(),
      errors: []
     }
      
    },
    methods: {
      submit() {
          const timeout = Math.floor(Math.random() * 1500) + 1 

          if (timeout > 1500) {
            //error
          } else {
            //axios post or 200
          }
          let config = {
            data : {
              'Nama' : this.name,
              'Nomor NIK' : this.nik,
              'Nomor KK' : this.kk,
              'Foto KTP' : this.uploadKtp,
              'Foto KK' : this.uploadKk,
              'Umur' : this.umur,
              'Alamat' : this.alamat,
              'RT' : this.alamatrt,
              'RW' : this.alamatrw,
              'Jenis Kelalmin' : this.jenisKelamin,
              'Penghasilan sebelum pandemi' : this.penghasilansbl,
              'Penghasilan sesudah pandemi' : this.penghasilansudah,
              'persetujuan' : this.checkbox
            }
          }
            console.log(config)
            this.clearForm()
            alert('terimakasih')
      },

      lopingRt() {
        let rt = []
        for(let i = 1; i <= 13; i++){
          rt.push(i)
        }
        return rt
      },

      lopingRw() {
        let rw = []
        for(let i = 1; i <= 9; i++){
          rw.push(i)
        }
        return rw
      },

      stringValidation(par) {
        let validasiHuruf = /^[a-zA-Z ]+$/;
        if(par.match(validasiHuruf)) {
          return false
        } else {
          return true
        } 
      },

      integerValidation(par){
        let validasiangka = /^[0-9]+$/;
          if(par.match(validasiangka)) {
            return false
          } else {
            return true
          } 
      },

      requaredValidation(){
        this.errors = [];
         
        if(this.name.length == '' || this.stringValidation(this.name)) {
          this.errors.push('Nama wajib di isi dan tidak boleh di isi dengan angka')
        }
        if(this.nik.length == '' || this.integerValidation(this.nik)) {
          this.errors.push('Nomor nik wajib di isi dan harus angka')
        }
        if(this.kk.length == '' || this.integerValidation(this.kk)) {
          this.errors.push('Nomor KK wajib di isi dan harus angka')
        }
        if(this.uploadKtp == null) {
          this.errors.push('KTP belum di input')
        }
        if(this.uploadKk == null) {
          this.errors.push('KK belum di input')
        }
        if(this.umur.length == '' || this.integerValidation(this.umur) || this.umur < 26) {
          this.errors.push('Umur minimal 25 tahun')
        }
        if(this.alamat.length == '' || this.alamat.length > 255) {
          this.errors.push('Alamat wajib di isi dan tidak boleh lebih dari 255 huruf')
        }
        if(this.alamatrw == '') {
          this.errors.push('Rw wajib di isi')
        }
        if(this.alamatrt == '') {
          this.errors.push('Rt wajib di isi')
        }
        if(this.penghasilansbl.length == '' || this.integerValidation(this.penghasilansbl)) {
          this.errors.push('Penghasilan sebelum pandemi wajib di isi dan harus angka')
        }
        if(this.penghasilansudah.length == '' || this.integerValidation(this.penghasilansudah)) {
          this.errors.push('Penghasilan sesudah pandemi wajib di isi dan harus angka')
        }
        if(this.checkbox == false) {
          this.errors.push('Klik persetujuan paling bawah')
        }
        if(this.errors == '') {
          this.submit()
        }
      },

      rulesWajibIsi(param) {
        if (param == null) {
            this.buttonStatus == 'notsubmit'
        } else {
          console.log(param)
        }
      },

      clearForm() {
        this.valid = true,
        this.name = '',
        this.nik =  '',
        this.kk = '',
        this.umur = '',
        this.alamat = '',
        this.penghasilansbl = '',
        this.penghasilansudah = ''
      },
    },

    components: {
     'header-kom' : Header
    }
};

</script>

<style>
  .background {
    background-color : #70CD94
  }
</style>
