<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
        <VuetifyLogo />
        <SearchBar />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Adopte un animal
        </v-card-title>
        <v-card-text>
          <p>Ils t'attendent tous !</p>
          <p>
            Déjà 29 adoptions !
          </p>
          <hr class="my-3">
        </v-card-text>
        <v-card-actions>
          <v-spacer /> 
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
