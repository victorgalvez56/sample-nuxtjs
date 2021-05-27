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
                      {{ $t('developer') }}
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>{{ $t('age') }}: 24
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>{{ $t('work_experience') }}: 6 {{ $t('years') }}
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>{{ $t('phone') }}: +51933336359
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>{{ $t('email') }}: victor.galvez56@gmail.com
                      </div>
                      <div>
                        <v-icon color="primary">
                          mdi-checkbox-marked-circle
                        </v-icon>{{ $t('country') }}: Perú
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
export default {
  data: () => ({
    fab: false,
    tab: null,
    model: null,
    language: '',
    dark: '',
    more: ['News', 'Maps', 'Books', 'Flights', 'Apps'],
    items: [
      {
        color: 'red lighten-2',
        icon: 'mdi-star'
      },
      {
        color: 'purple darken-1',
        icon: 'mdi-book-variant'
      },
      {
        color: 'green lighten-1',
        icon: 'mdi-airballoon'
      },
      {
        color: 'indigo',
        icon: 'mdi-buffer'
      }
    ],
    portfolio: [
      {
        img: '',
        title: '',
        text: ''
      }
    ],
    length: 4,
    onboarding: 0,
    portfolios: [
      {
        img: 'quipubeer-landing.png',
        title: 'QuipuBeer',
        text: ''
      },
      {
        img: 'anunciadev-landing.png',
        title: 'AnunciaDev',
        text: ''
      },
      {
        img: 'sistemainventario-landing.png',
        title: 'Sistema Inventario',
        text: ''
      },
      {
        img: 'presupuestos-landing.png',
        title: 'Sistema Valoraciones Colegio Prescott',
        text: ''
      }
    ],
    panelsSkills: [
      {
        text: 'FrontEnd'
      },
      {
        text: 'BackEnd'
      },
      {
        text: 'Others'
      }
    ],
    technologiesFront: [
      {
        svg: 'html5.svg'
      },
      {
        svg: 'css3.svg'
      },
      {
        svg: 'javascript.svg'
      },
      {
        svg: 'jquery-2.svg'
      },
      {
        svg: 'typescript.svg'
      },
      {
        svg: 'vue.svg'
      },
      {
        svg: 'vuetify.svg'
      },
      {
        svg: 'quasar.png'
      },
      {
        svg: 'nuxt-logo.png'
      }
    ],
    technologiesBackend: [
      {
        svg: 'laravel.svg'
      },
      {
        svg: 'codeigniter.svg'
      },
      {
        svg: 'php.svg'
      },
      {
        svg: 'java.png'
      },
      {
        svg: 'firebase.svg'
      }
    ],
    technologiesOthers: [
      {
        svg: 'euroidiomas.png'
      },
      {
        svg: 'docker.svg'
      },
      {
        svg: 'figma.png'
      },
      {
        svg: 'google-cloud-2.svg'
      },
      {
        svg: 'git.svg'
      }
    ]
  }),
  created () {
    this.language = this.$i18n.locale
    this.dark = true
  },
  methods: {
    onScroll (e) {
      if (typeof window === 'undefined') { return }
      const top = window.pageYOffset || e.target.scrollTop || 0
      this.fab = top > 20
    },
    toTop () {
      this.$vuetify.goTo(0)
    },
    next () {
      this.onboarding = this.onboarding + 1 === this.length
        ? 0
        : this.onboarding + 1
    },
    prev () {
      this.onboarding = this.onboarding - 1 < 0
        ? this.length - 1
        : this.onboarding - 1
    },
    onToggleLocale (locale) {
      this.$i18n.locale = locale
      this.locale = locale
      this.language = this.$i18n.locale
    },
    onToggleTheme () {
      if (this.$vuetify.theme.dark) {
        this.$vuetify.theme.dark = false
      } else {
        this.$vuetify.theme.dark = true
      }
    }
  }
}
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
