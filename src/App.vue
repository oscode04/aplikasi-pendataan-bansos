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
                :rules="rules"
                accept="image/png, image/jpeg, image/bmp"
                placeholder="Pick an avatar"
                prepend-icon="mdi-camera"
                label="Masukan foto KTP"
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
                :rules="rules"
                accept="image/png, image/jpeg, image/bmp"
                placeholder="Pick an avatar"
                prepend-icon="mdi-camera"
                label="Masukan foto KK"
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
              <h3>{{ radios || 'null' }}</h3>
                <v-radio-group
                  v-model="radios"
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

    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
   data: () => ({
      valid: false,
      name: '',
      nik: '',
      kk: '',
      umur:'',
      alamat:'',
      radios: null,
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
    }),
};

</script>
