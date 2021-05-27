<template>
  <v-app id="inspire">
    <div class="image">
      <v-container>
        <v-row no-gutters>
          <v-col cols="12">
            <v-col sm="4">
              <v-hover>
                <template v-slot:default="{ hover }">
                  <v-card :elevation="hover ? 24 : 6" class="mx-auto pa-6">
                    <template slot="progress">
                      <v-progress-linear
                        color="deep-purple"
                        height="10"
                        indeterminate
                      />
                    </template>

                    <v-img height="100%" src="profile.jpg" />

                    <v-card-title class="primary--text">
                      Víctor Gálvez
                    </v-card-title>

                    <v-card-subtitle>
                      Developer
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>Edad: 24
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>Años: 6 
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>Teléfono: +51933336359
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>Teléfono: +51933336359
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>Teléfono: +51933336359
                      </div>
                    </v-card-subtitle>
                    <v-card-text />
                  </v-card>
                </template>
              </v-hover>
            </v-col>
          </v-col>
        </v-row>
        <v-btn
          v-show="fab"
          v-scroll="onScroll"
          fab
          dark
          fixed
          bottom
          right
          color="#2e8fad"
          @click="toTop"
        >
          <v-icon>mdi-chevron-up</v-icon>
        </v-btn>
      </v-container>

    </div>
  </v-app>
</template>

<script>
export default {};
</script>

<style>
.image {
  background: url("~static/bg.jpg");
  background-position: 50%;
  background-size: cover;
  background-repeat: no-repeat;
  height: 100%;
}
</style>
