<template>
    
  <v-container>
  <v-card
    class="mx-auto"
    max-width="80%"
  >
    <v-card-text>
      <p class="text-h5 text--primary">
        {{ nama }}
      </p>
      <v-form
      ref="form"
      v-model="valid"
      lazy-validation
      >
        <div>
          <v-row>
          <v-col
          cols="12"
          md="12"
          > 
              <v-text-field
                v-model="isi"
                
                :label= this.label
                required
              ></v-text-field>
          </v-col>
          </v-row>
        </div>
      </v-form>

    </v-card-text>
  </v-card>
  </v-container>
</template>

<script> 
export default {
    data: () => ({
      valid: false,
      isi: '',
      // nameRules: [
      //   v => !!v || 'Name is required',
      // ],
      // inirules: [
      //   v => !!v || 'this.rules',
      // ],
    }),
    props : [
      'nama',
      'label',
      ]
}
</script>
