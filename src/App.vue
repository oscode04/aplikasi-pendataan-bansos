<template>
  <v-app>
    <v-main>
      <v-container grid-list-lg>
        <v-card
          class="mx-auto"
          max-width="80%"
        >
      <v-card-text>
        <p class="text-h4 text--primary text-center justify-center mt-5">
          <b>PENDATAAN BANSOS</b>
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
            <p>
              Pilih jenis kelamin
            </p>
          </v-card-text>
          
        <v-form v-model="valid" >
          <v-container>
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

    <!-- tombol submit -->
    <v-container>
      <div class="text-center mb-5">
          <v-btn rounded color="primary accent-3" dark @click="submit"  width="80%" height="50"> <h1>Submit</h1> </v-btn>
      </div>
    </v-container>
    </v-main>
  </v-app>
</template>

<script>

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
      jenisKelamin: null,
      penghasilansudah:'',
      penghasilansbl:'',
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
      ],
      penghasilanRules: [
        v => !!v || 'penghasilan wajib di isi',
      ],
      rules: [
        value => !value || value.size < 2000000 || 'ukuran foto tidak boleh lebih dari 2 MB!',
      ],
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
          // let formData = new FormData()
          // formData.append('name', this.name)
          // formData.append('nik', this.nik)
          // formData.append('ktp', file)
          // let config = {
          //     nama : this.name,
          //     nik : this.nik,
          //     kk : this.kk,
          //     uploadKk : this.uploadKk,
          //     umur : this.umur,
          //     alamat : this.alamat,
          //     jenisKelamin : this.jenisKelamin,
          //     penghasilansudah : this.penghasilansudah,
          //     penghasilansbl : this.penghasilansbl,
          // };

          let config = {
            data : {
              'Nama' : this.name,
              'Nomor NIK' : this.nik,
              'Nomor KK' : this.kk,
              'Foto KTP' : this.uploadKtp,
              'Foto KK' : this.uploadKk,
              'Umur' : this.umur,
              'Alamat' : this.alamat,
              'Jenis Kelalmin' : this.jenisKelamin,
              'Penghasilan sebelum pandemi' : this.penghasilansbl,
              'Penghasilan sesudah pandemi' : this.penghasilansudah
            }
          }
          console.log(config)
      },
      uploadFile(event) {
        let file = event.target.files[0].name
        return file
      }
    }
};

</script>
