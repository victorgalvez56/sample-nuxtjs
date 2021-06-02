<template>
  <v-app id="inspire">
    <div class="image">
      <v-container>
        <v-row>
          <v-col cols="12" sm="4">
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
                    {{ $t("developer") }}
                    <div>
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("age") }}: 24
                    </div>
                    <div>
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("work_experience") }}: 6 {{ $t("years") }}
                    </div>
                    <div>
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("phone") }}: +51933336359
                    </div>
                    <div>
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("email") }}: victor.galvez56@gmail.com
                    </div>
                    <div>
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("country") }}: Perú
                    </div>
                  </v-card-subtitle>
                  <v-card-text />
                </v-card>
              </template>
            </v-hover>
          </v-col>
          <v-col cols="12" sm="8">
            <v-hover>
              <template v-slot:default="{ hover }">
                <v-card :elevation="hover ? 24 : 6" class="mx-auto pa-6">
                  <v-tabs v-model="tab" show-arrows right>
                    <v-tab> {{ $t("about_me") }}</v-tab>
                    <v-tab> {{ $t("portfolio") }} </v-tab>
                    <v-tab> {{ $t("skills") }} </v-tab>
                    <v-menu v-if="more.length" bottom left>
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn
                          text
                          class="align-self-center mr-4"
                          v-bind="attrs"
                          color="grey darken-1"
                          v-on="on"
                        >
                          {{ $t("options") }}
                          <v-icon right>
                            mdi-menu-down
                          </v-icon>
                        </v-btn>
                      </template>
                      <v-list>
                        <v-list-item-group>
                          <v-list-item
                            v-if="$vuetify.theme.dark"
                            @click="onToggleTheme()"
                          >
                            <v-list-item-content>
                              <v-icon>mdi-lightbulb-on-outline</v-icon>
                            </v-list-item-content>
                          </v-list-item>
                          <v-list-item
                            v-if="!$vuetify.theme.dark"
                            @click="onToggleTheme()"
                          >
                            <v-list-item-content>
                              <v-icon>mdi-lightbulb-off-outline</v-icon>
                            </v-list-item-content>
                          </v-list-item>

                          <v-list-item
                            v-if="language == 'en'"
                            @click="onToggleLocale('es')"
                          >
                            <v-list-item-content>
                              <v-img src="es.svg" contain max-height="20px" />
                            </v-list-item-content>
                          </v-list-item>
                          <v-list-item
                            v-if="language == 'es'"
                            @click="onToggleLocale('en')"
                          >
                            <v-list-item-content>
                              <v-img src="en.svg" contain max-height="20px" />
                            </v-list-item-content>
                          </v-list-item>
                        </v-list-item-group>
                      </v-list>
                    </v-menu>
                  </v-tabs>
                  <v-tabs-items v-model="tab">
                    <v-container class="spacing-playground" fluid>
                      <v-tab-item>
                        <v-card flat min-height="465px">
                          <v-card-title class="primary--text">
                            About me
                          </v-card-title>
                          <v-card-text>
                            <div class="text-justify">
                              Hi, I’m Victor. Nice to meet you. Since beginning
                              my journey as a freelance designer nearly 10 years
                              ago, I've done remote work for agencies, consulted
                              for startups, and collaborated with talented
                              people to create digital products for both
                              business and consumer use. I'm quietly confident,
                              naturally curious, and perpetually working on
                              improving my chops one design problem at a time.
                            </div>
                            <v-divider />
                            <v-expansion-panels>
                              <v-expansion-panel>
                                <v-expansion-panel-header class="primary--text">
                                  Formación Profesional
                                  <template v-slot:actions>
                                    <v-icon color="green">
                                      $expand
                                    </v-icon>
                                  </template>
                                </v-expansion-panel-header>
                                <v-expansion-panel-content>
                                  <v-timeline align-top dense>
                                    <v-timeline-item
                                      color="pink"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Bachiller</strong>
                                          <div class="caption">
                                            Ingeniería de Sistemas en
                                            Universidad Tecnológica del Perú -
                                            Arequipa
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                  </v-timeline>
                                  <v-timeline align-top dense>
                                    <v-timeline-item
                                      color="pink"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Inglés Intermedio con
                                            certificación</strong
                                          >
                                          <div class="caption">
                                            Euroidiomas: Institución de inglés y
                                            otros idiomas.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                  </v-timeline>
                                </v-expansion-panel-content>
                              </v-expansion-panel>
                              <v-expansion-panel>
                                <v-expansion-panel-header class="primary--text">
                                  Experiencia Laboral
                                  <template v-slot:actions>
                                    <v-icon color="green">
                                      $expand
                                    </v-icon>
                                  </template>
                                </v-expansion-panel-header>
                                <v-expansion-panel-content>
                                  <v-timeline align-top dense>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Acist Peru S.A.C.</strong>
                                          <div class="caption">
                                            Desarrollo de sistemas webs usando
                                            Laravel + VuetifyJS + NuxtJs.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Itesur S.A.C.</strong>
                                          <div class="caption">
                                            Desarrollo de sistemas webs usando
                                            Laravel.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Colegio Anglo Americano
                                            Prescott</strong
                                          >
                                          <div class="caption">
                                            Desarrollo de sistemas webs usando
                                            Laravel.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Softia</strong>
                                          <div class="caption">
                                            Desarrollo de sistemas webs usando
                                            Java Spring MVC.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Instituto Macro Perú</strong>
                                          <div class="caption">
                                            Elaboración de Sistema Específico de
                                            certificados.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Turbo Gaming Center</strong>
                                          <div class="caption">
                                            Elaboración Sistema Específico de
                                            Ventas e Inventario empresa.
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Poder Judicial</strong>
                                          <div class="caption">
                                            Documentación y análisis en el
                                            Proyecto de Interoperabilidad de
                                            Operadores de Justicia, Sistema SIOJ
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="indigo darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>EsSalud</strong>
                                          <div class="caption">
                                            Documentación y análisis en el
                                            Sistema Control de Expedientes- Área
                                            Logística
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                  </v-timeline>
                                </v-expansion-panel-content>
                              </v-expansion-panel>
                              <v-expansion-panel>
                                <v-expansion-panel-header class="primary--text">
                                  Hackathones
                                  <template v-slot:actions>
                                    <v-icon color="green">
                                      $expand
                                    </v-icon>
                                  </template>
                                </v-expansion-panel-header>
                                <v-expansion-panel-content>
                                  <v-timeline align-top dense>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Hackathon Oracle Apex 2020
                                            Latinoamerica</strong
                                          >
                                          <div class="caption">
                                            Segundo puesto nivel Latinoamerica.
                                            Proyecto “Plataforma educativa
                                            DidactiCloud”.
                                            <a
                                              target="_blank"
                                              href="https://blogs.oracle.com/apex/apexhack20:-primer-hackaton-en-latinoam%c3%a9rica"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Hackathon Comercio Perú
                                            2020</strong
                                          >
                                          <div class="caption">
                                            Participación a través del proyecto
                                            de “Red Social para conocimiento de
                                            candidatos presidenciales”.
                                            <a
                                              target="_blank"
                                              href="https://elcomercio.pe/tecnologia/hackathon-jovenes-disenaran-soluciones-centradas-en-el-voto-informado-tecnologia-noticia/?ref=ecr"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Hackathon La positiva 2019</strong
                                          >
                                          <div class="caption">
                                            Participación a través del proyecto
                                            de “Detección de nivel de estrés a
                                            través de reconocimiento facial”.
                                            <a
                                              target="_blank"
                                              href="https://open.pucp.edu.pe/noticias/ganadores-de-la-iv-hackathon-la-positiva-convertiran-sus-ideas-en-startups/"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Hackathon Perumin 2019</strong
                                          >
                                          <div class="caption">
                                            Participación a través del proyecto
                                            de “La supervisión y monitoreo del
                                            estado de salud y ubicación de
                                            trabajadores en tiempo real durante
                                            sus actividades de explotación
                                            minera subterránea”
                                            <a
                                              target="_blank"
                                              href="https://desdeadentro.pe/main/edicion/66/articulos/premian-a-ganadores-de-la-6-hackaton-2019"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong
                                            >Hackathon El Comercio 2019</strong
                                          >
                                          <div class="caption">
                                            Segundo puesto a nivel nacional en
                                            solución innovadora y tecnológica
                                            para el problema de la denuncias y
                                            delincuencia.
                                            <a
                                              target="_blank"
                                              href="https://elcomercio.pe/tecnologia/estoyalerta-jovenes-peruanos-disenan-una-red-social-contra-la-delincuencia-noticia/"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                    <v-timeline-item
                                      color="green darken-4"
                                      small
                                      icon="mdi-star"
                                    >
                                      <v-row class="pt-1">
                                        <v-col>
                                          <strong>Apuesta por ti</strong>
                                          <div class="caption">
                                            Participación en IV Edición del
                                            Premio al Emprendedor Universitario.
                                            <a
                                              target="_blank"
                                              href="https://www.facebook.com/UTPSedeArequipa/posts/1229404533909287/"
                                              >Ver Noticia</a
                                            >
                                          </div>
                                        </v-col>
                                      </v-row>
                                    </v-timeline-item>
                                  </v-timeline>
                                </v-expansion-panel-content>
                              </v-expansion-panel>
                            </v-expansion-panels>
                          </v-card-text>
                        </v-card>
                      </v-tab-item>
                      <v-tab-item>
                        <v-card flat min-height="465px">
                          <v-window v-model="onboarding" vertical>
                            <v-window-item
                              v-for="portfolio in portfolios"
                              :key="`card-${portfolio}`"
                              show-arrows-on-hover="true"
                            >
                              <v-card class="mx-auto">
                                <v-img
                                  :src="portfolio.img"
                                  contain
                                  max-height="295"
                                />

                                <v-card-text>
                                  <h2 class="title primary--text">
                                    {{ portfolio.title }}
                                  </h2>
                                  Travel to the best outdoor experience on
                                  planet Earth. A vacation you will never
                                  forget!
                                </v-card-text>
                              </v-card>
                            </v-window-item>
                          </v-window>

                          <v-card-actions class="justify-space-between">
                            <v-btn text @click="prev">
                              <v-icon>mdi-chevron-left</v-icon>
                            </v-btn>
                            <v-item-group
                              v-model="onboarding"
                              class="text-center"
                              mandatory
                            >
                              <v-item
                                v-for="n in length"
                                :key="`btn-${n}`"
                                v-slot="{ active, toggle }"
                              >
                                <v-btn
                                  :input-value="active"
                                  icon
                                  @click="toggle"
                                >
                                  <v-icon>mdi-record</v-icon>
                                </v-btn>
                              </v-item>
                            </v-item-group>
                            <v-btn text @click="next">
                              <v-icon>mdi-chevron-right</v-icon>
                            </v-btn>
                          </v-card-actions>
                        </v-card>
                      </v-tab-item>
                      <v-tab-item>
                        <v-card flat>
                          <v-container class=" lighten-5">
                            <v-row justify="center">
                              <v-expansion-panels popout>
                                <v-expansion-panel>
                                  <v-expansion-panel-header
                                    class="primary--text"
                                  >
                                    Frontend
                                  </v-expansion-panel-header>
                                  <v-expansion-panel-content>
                                    <v-col
                                      v-for="technology in technologiesFront"
                                      :key="technology"
                                      cols="3"
                                    >
                                      <v-container>
                                        <v-img
                                          :src="technology.svg"
                                          height="100"
                                          contain
                                        />
                                      </v-container>
                                    </v-col>
                                  </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                  <v-expansion-panel-header
                                    class="primary--text"
                                  >
                                    Backend
                                  </v-expansion-panel-header>
                                  <v-expansion-panel-content>
                                    <v-col
                                      v-for="technology in technologiesBackend"
                                      :key="technology"
                                      cols="3"
                                    >
                                      <v-container>
                                        <v-img
                                          :src="technology.svg"
                                          height="100"
                                          contain
                                        />
                                      </v-container>
                                    </v-col>
                                  </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                  <v-expansion-panel-header
                                    class="primary--text"
                                  >
                                    Others
                                  </v-expansion-panel-header>
                                  <v-expansion-panel-content>
                                    <v-col
                                      v-for="technology in technologiesOthers"
                                      :key="technology"
                                      cols="3"
                                    >
                                      <v-container>
                                        <v-img
                                          :src="technology.svg"
                                          height="100"
                                          contain
                                        />
                                      </v-container>
                                    </v-col>
                                  </v-expansion-panel-content>
                                </v-expansion-panel>
                              </v-expansion-panels>
                            </v-row>
                          </v-container>
                        </v-card>
                      </v-tab-item>
                    </v-container>
                  </v-tabs-items>
                </v-card>
              </template>
            </v-hover>
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
    language: "",
    dark: "",
    more: ["News", "Maps", "Books", "Flights", "Apps"],
    items: [
      {
        color: "red lighten-2",
        icon: "mdi-star"
      },
      {
        color: "purple darken-1",
        icon: "mdi-book-variant"
      },
      {
        color: "green lighten-1",
        icon: "mdi-airballoon"
      },
      {
        color: "indigo",
        icon: "mdi-buffer"
      }
    ],
    portfolio: [
      {
        img: "",
        title: "",
        text: ""
      }
    ],
    length: 4,
    onboarding: 0,
    portfolios: [
      {
        img: "quipubeer-landing.png",
        title: "QuipuBeer",
        text: ""
      },
      {
        img: "anunciadev-landing.png",
        title: "AnunciaDev",
        text: ""
      },
      {
        img: "sistemainventario-landing.png",
        title: "Sistema Inventario",
        text: ""
      },
      {
        img: "presupuestos-landing.png",
        title: "Sistema Valoraciones Colegio Prescott",
        text: ""
      }
    ],
    panelsSkills: [
      {
        text: "FrontEnd"
      },
      {
        text: "BackEnd"
      },
      {
        text: "Others"
      }
    ],
    technologiesFront: [
      {
        svg: "html5.svg"
      },
      {
        svg: "css3.svg"
      },
      {
        svg: "javascript.svg"
      },
      {
        svg: "jquery-2.svg"
      },
      {
        svg: "typescript.svg"
      },
      {
        svg: "vue.svg"
      },
      {
        svg: "vuetify.svg"
      },
      {
        svg: "quasar.png"
      },
      {
        svg: "nuxt-logo.png"
      }
    ],
    technologiesBackend: [
      {
        svg: "laravel.svg"
      },
      {
        svg: "codeigniter.svg"
      },
      {
        svg: "php.svg"
      },
      {
        svg: "java.png"
      },
      {
        svg: "firebase.svg"
      }
    ],
    technologiesOthers: [
      {
        svg: "euroidiomas.png"
      },
      {
        svg: "docker.svg"
      },
      {
        svg: "figma.png"
      },
      {
        svg: "google-cloud-2.svg"
      },
      {
        svg: "git.svg"
      }
    ]
  }),
  created() {
    this.language = this.$i18n.locale;
    this.dark = true;
  },
  methods: {
    onScroll(e) {
      if (typeof window === "undefined") {
        return;
      }
      const top = window.pageYOffset || e.target.scrollTop || 0;
      this.fab = top > 20;
    },
    toTop() {
      this.$vuetify.goTo(0);
    },
    next() {
      this.onboarding =
        this.onboarding + 1 === this.length ? 0 : this.onboarding + 1;
    },
    prev() {
      this.onboarding =
        this.onboarding - 1 < 0 ? this.length - 1 : this.onboarding - 1;
    },
    onToggleLocale(locale) {
      this.$i18n.locale = locale;
      this.locale = locale;
      this.language = this.$i18n.locale;
    },
    onToggleTheme() {
      if (this.$vuetify.theme.dark) {
        this.$vuetify.theme.dark = false;
      } else {
        this.$vuetify.theme.dark = true;
      }
    }
  }
};
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
