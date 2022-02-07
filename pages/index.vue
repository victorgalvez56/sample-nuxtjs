<template>
  <v-app id="inspire">
    <div class="image">
      <v-container>
        <v-row>
          <v-col cols="12" sm="4" height="100vh">
            <v-hover>
              <template v-slot:default="{ hover }">
                <v-card
                  :elevation="hover ? 12 : 3"
                  class="mx-auto pa-6"
                  height="100vh"
                >
                  <v-img src="profile.jpg" height="60%" />

                  <v-card-title class="primary--text">
                    Víctor Gálvez Cha.
                  </v-card-title>

                  <v-card-subtitle class="pb-0">
                    {{ $t("developer") }}
                    <div class="mt-1">
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("work_experience") }}: 6 {{ $t("years") }}
                    </div>
                    <div class="mt-1">
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("phone") }}: +51933336359
                    </div>
                    <div class="mt-1">
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("email") }}: victor.galvez56@gmail.com
                    </div>
                    <div class="mt-1">
                      <v-icon color="primary">
                        mdi-checkbox-marked-circle </v-icon
                      >{{ $t("country") }}: Perú
                    </div>
                    <div class="d-flex justify-center mt-2" flat tile>
                      <v-btn
                        class="mx-1"
                        v-for="network in social_networks"
                        :key="network"
                        fab
                        dark
                        small
                        :color="network.color"
                        :href="network.url"
                        target="_blank"
                        download=""
                      >
                        <v-icon>{{ `mdi-${network.icon}` }}</v-icon>
                      </v-btn>
                    </div>
                  </v-card-subtitle>
                </v-card>
              </template>
            </v-hover>
          </v-col>
          <v-col cols="12" sm="8" height="100vh">
            <v-card
              :elevation="hover ? 12 : 3"
              class="mx-auto pa-6"
              height="100%"
            >
              <v-toolbar elevation="0" right>
                <template v-slot:extension>
                  <v-tabs v-model="tab" fixed-tabs show-arrows right>
                    <v-tab> {{ $t("about_me") }}</v-tab>
                    <v-tab> {{ $t("portfolio") }} </v-tab>
                    <v-tab> {{ $t("skills") }} </v-tab>
                    <v-menu v-if="more.length" bottom left>
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn
                          text
                          class="align-self-center mr-4"
                          v-bind="attrs"
                          v-on="on"
                        >
                          {{ $t("options") }}

                          <v-icon right> mdi-menu-down </v-icon>
                        </v-btn>
                      </template>

                      <v-list class="grey lighten-3">
                        <v-list-item-group>
                          <v-list-item
                          color="grey"
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
                </template>
              </v-toolbar>

              <v-tabs-items v-model="tab">
                <v-container class="spacing-playground" fluid>
                  <v-tab-item>
                    <v-card flat min-height="465px">
                      <v-card-title class="primary--text">
                        {{ $t("about_me") }}
                      </v-card-title>
                      <v-card-text>
                        <div class="text-justify">
                          {{ $t("description_about_me") }}
                        </div>
                        <v-divider class="pa-md-4 mx-lg-auto"></v-divider>
                        <v-expansion-panels>
                          <v-expansion-panel>
                            <v-expansion-panel-header class="primary--text">
                              {{ $t("vocational_training") }}
                              <template v-slot:actions>
                                <v-icon color="green"> $expand </v-icon>
                              </template>
                            </v-expansion-panel-header>
                            <v-expansion-panel-content class="padding-g">
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
                                        Ingeniería de Sistemas en Universidad
                                        Tecnológica del Perú - Arequipa
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
                              {{ $t("work_experience") }}
                              <template v-slot:actions>
                                <v-icon color="green"> $expand </v-icon>
                              </template>
                            </v-expansion-panel-header>
                            <v-expansion-panel-content class="padding-g">
                              <v-timeline align-top dense>
                                <v-timeline-item
                                  color="indigo darken-4"
                                  small
                                  icon="mdi-star"
                                >
                                  <v-row class="pt-1">
                                    <v-col>
                                      <strong>Lixsys (Chile)</strong>
                                      <div class="caption">
                                        Desarrollo de aplicaciones para miles de
                                        usuarios en PHP, ReactJS, Capacitor,
                                        Ionic.
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
                                      <strong>HanuFit (Chile)</strong>
                                      <div class="caption">
                                        Desarrollo de aplicación para miles de
                                        usuarios en ReactJS + NodeJS +
                                        Capacitor.
                                        <a href="https://www.hanufit.com/"
                                          >Aquí</a
                                        >
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
                                        Desarrollo de sistemas webs usando Java
                                        Spring MVC.
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
                                        certificados usando Codeigniter.
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
                                        Elaboración Sistema Específico de Ventas
                                        e Inventario empresa usando Codeigniter.
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
                                        Documentación y análisis en el Proyecto
                                        de Interoperabilidad de Operadores de
                                        Justicia, Sistema SIOJ
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
                                        Documentación y análisis en el Sistema
                                        Control de Expedientes- Área Logística
                                      </div>
                                    </v-col>
                                  </v-row>
                                </v-timeline-item>
                              </v-timeline>
                            </v-expansion-panel-content>
                          </v-expansion-panel>
                          <v-expansion-panel style="padding: 0 0 0">
                            <v-expansion-panel-header class="primary--text">
                              Hackathones
                              <template v-slot:actions>
                                <v-icon color="green"> $expand </v-icon>
                              </template>
                            </v-expansion-panel-header>
                            <v-expansion-panel-content class="padding-g">
                              <v-timeline align-top dense>
                                <v-timeline-item
                                  color="green darken-4"
                                  small
                                  icon="mdi-star"
                                >
                                  <v-row class="pt-1">
                                    <v-col>
                                      <strong
                                        >Hackathon Comercio Perú 2021
                                      </strong>
                                      <div class="caption">
                                        Primer puesto nivel nacional. Proyecto
                                        “Nansuyai”.
                                        <a
                                          target="_blank"
                                          href="https://elcomercio.pe/tecnologia/tecnologia-jovenes-peruanos-disenan-una-app-para-combatir-la-violencia-de-genero-noticia/"
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
                                        >Hackathon Comercio Perú 2020</strong
                                      >
                                      <div class="caption">
                                        Participación a través del proyecto de
                                        “Red Social para conocimiento de
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
                                        Participación a través del proyecto de
                                        “Detección de nivel de estrés a través
                                        de reconocimiento facial”.
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
                                      <strong>Hackathon Perumin 2019</strong>
                                      <div class="caption">
                                        Participación a través del proyecto de
                                        “La supervisión y monitoreo del estado
                                        de salud y ubicación de trabajadores en
                                        tiempo real durante sus actividades de
                                        explotación minera subterránea”
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
                                        solución innovadora y tecnológica para
                                        el problema de la denuncias y
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
                                        Participación en IV Edición del Premio
                                        al Emprendedor Universitario.
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

                              {{ portfolio.text }}
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
                            v-for="portfolio in portfolios"
                            :key="`btn-${portfolio}`"
                            v-slot="{ active, toggle }"
                          >
                            <v-btn :input-value="active" icon @click="toggle">
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
                      <v-container class="lighten-5">
                        <v-row justify="center">
                          <v-expansion-panels popout>
                            <v-expansion-panel>
                              <v-expansion-panel-header class="primary--text">
                                Frontend
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-row>
                                  <v-col
                                    v-for="technology in technologiesFront"
                                    :key="technology"
                                    cols="12"
                                    sm="4"
                                  >
                                    <v-container>
                                      <v-img
                                        :src="technology.svg"
                                        height="100"
                                        contain
                                      />
                                    </v-container>
                                  </v-col>
                                </v-row>
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                            <v-expansion-panel>
                              <v-expansion-panel-header class="primary--text">
                                Backend
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-row>
                                  <v-col
                                    v-for="technology in technologiesBackend"
                                    :key="technology"
                                    cols="12"
                                    sm="4"
                                  >
                                    <v-container>
                                      <v-img
                                        :src="technology.svg"
                                        height="100"
                                        contain
                                      />
                                    </v-container>
                                  </v-col>
                                </v-row>
                              </v-expansion-panel-content>
                            </v-expansion-panel>
                            <v-expansion-panel>
                              <v-expansion-panel-header class="primary--text">
                                Others
                              </v-expansion-panel-header>
                              <v-expansion-panel-content>
                                <v-row>
                                  <v-col
                                    v-for="technology in technologiesOthers"
                                    :key="technology"
                                    cols="12"
                                    sm="4"
                                  >
                                    <v-container>
                                      <v-img
                                        :src="technology.svg"
                                        height="100"
                                        contain
                                      />
                                    </v-container>
                                  </v-col>
                                </v-row>
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


          </v-col>
        </v-row>
        <v-btn
          v-show="fab"
          v-scroll="onScroll"
          small
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
        <v-btn
          v-scroll="onScroll"
          small
          fab
          dark
          fixed
          bottom
          left
          class="float"
          color="#25d366"
          @click="toTop"
          href="https://api.whatsapp.com/send?phone=51933336359&text=Hola"
        >
          <v-icon>mdi-whatsapp</v-icon>
        </v-btn>
        <!-- <a href="https://api.whatsapp.com/send?phone=51933336359&text=Hola" class="float" target="_blank">
        </a> -->
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
        icon: "mdi-star",
      },
      {
        color: "purple darken-1",
        icon: "mdi-book-variant",
      },
      {
        color: "green lighten-1",
        icon: "mdi-airballoon",
      },
      {
        color: "indigo",
        icon: "mdi-buffer",
      },
    ],
    portfolio: [
      {
        img: "",
        title: "",
        text: "",
      },
    ],
    length: 4,
    onboarding: 0,
    portfolios: [
      {
        img: "nansuyai.PNG",
        title: "Nansuyai",
        text: "App móvil para brindar seguridad y asistencia psicológicas a mujeres que han sufrido algún tipo de violencia. El app se conecta a una pulsera inteligente que brinda información de la ubicación en tiempo real y brinda alertas.",
      },
      {
        img: "insulina.PNG",
        title: "Novo Cine 2",
        text: "Sistema web responsive para pedir comida en estacionamientos, realizar preguntas y encuestas sobre lo que se proyecta.",
      },
      {
        img: "cajalosandes.PNG",
        title: "Corrida Caja los Andes",
        text: "App móvil en androis y ios para registrar el tracking de las corridas rastreando tu distancia, ritmo y tiempo. Mantiene tu mejor carrera actualizada y te muestra en tiempo real el recorrido. ",
      },
      {
        img: "desafio-glp.PNG",
        title: "Desafío GLP",
        text: "Plataforma Educativa streamming para el aprendizaje de doctores sobre la diabetes para doctores de diferentes países de LATAM",
      },
      {
        img: "hanu-fit.PNG",
        title: "HanuFit",
        text: "Sistema web PWA, Se utilizó ReactJS + NodeJS + Capacitor para la versión Mobile. Para entrenamiento, nutrición y relajación para miles de usuarios",
      },
      {
        img: "nuevoamanecer.PNG",
        title: "Un nuevo amanecer",
        text: "Sistema informativo de eventos en diferentes ciudades de Chile. ",
      },
      {
        img: "admin-system-factur.png",
        title: "Sistema para crear Tenant",
        text: "Sistema con arquitectura de software Multitenant, está arquitectura permite a una sola instancia de software servir a muchos clientes. En otras palabras este software es una panel para crear clientes con su propia base de datos, lógica y requerimientos. Separando la información sensible de cada uno y que solo sea visible por ellos.",
      },
      {
        img: "bizag-tenant.png",
        title: "Tenant de Facturación BIZAG",
        text: "Sistema para facturación electrónica usando VueJS en frontend y Laravel en Backend.",
      },

      {
        img: "cover-prime.png",
        title: "Cover Prime",
        text: "Landing Page para empresa de covertizos con el fin de promocionar sus productos para alcanzar a sus clientes.",
      },
      {
        img: "sistema-personal-acist.png",
        title: "Bizag Personal",
        text: "Sistema para control de personal usando NuxtJS en frontend y Laravel en Backend",
      },
      {
        img: "quipubeer-landing.png",
        title: "QuipuBeer",
        text: "Landing Page para empresa de cervezas artesanales con el fin de promocionar sus productos para alcanzar a sus clientes.",
      },
      {
        img: "supervisionobra.png",
        title: "Supervisión de Obras",
        text: "Sistema para la supervisión de obras en Minera Luren S.A.C. Se realizó con VueJS en frontend y Laravel en Backend para diferentes módulos cómo programación de fechas, estados de obras,etc.",
      },
      {
        img: "anunciadev-landing.png",
        title: "AnunciaDev",
        text: "Sistema para anuncios de empresas a nivel latinoamerica en Itesur S.A.C. Se realizó con Laravel + JQuery.",
      },
      {
        img: "sistemainventario-landing.png",
        title: "Sistema Inventario",
        text: "Sistema para control de almacén en empresa TurboGamingCenter se realizó con PHP Codeigniter los diferentes módulos de reportes y charts.",
      },
      {
        img: "control-personal.png",
        title: "Sistema Control Persona para Ejército del Perú",
        text: "Sistema para control de personal en Ejército del Perú se realizó con PHP Codeigniter los diferentes requerimientos cómo código de barras, control de salubridad, etc.",
      },
      {
        img: "presupuestos-landing.png",
        title: "Sistema Valoraciones Colegio Prescott",
        text: "Sistema para valoración de personal en Colegio Anglo Americano Prescott se realizó con PHP Codeigniter los diferentes requerimientos cómo promedio y ranking de personal.",
      },
    ],
    panelsSkills: [
      {
        text: "FrontEnd",
      },
      {
        text: "BackEnd",
      },
      {
        text: "Others",
      },
    ],
    technologiesFront: [
      {
        svg: "react.png",
      },
      {
        svg: "vue.svg",
      },
      {
        svg: "vuetify.svg",
      },
      {
        svg: "boostrap.png",
      },
      {
        svg: "quasar.png",
      },
      {
        svg: "nuxt-logo.png",
      },
      {
        svg: "html5.svg",
      },
      {
        svg: "css3.svg",
      },
      {
        svg: "javascript.svg",
      },
      {
        svg: "jquery-2.svg",
      },
      {
        svg: "typescript.svg",
      },
    ],
    technologiesBackend: [
      {
        svg: "laravel.svg",
      },
      {
        svg: "cakephp.jpg",
      },
      {
        svg: "codeigniter.svg",
      },
      {
        svg: "php.svg",
      },
      {
        svg: "java.png",
      },
      {
        svg: "node-js.png",
      },
    ],
    technologiesOthers: [
      {
        svg: "euroidiomas.png",
      },
      {
        svg: "figma.png",
      },
      {
        svg: "google-cloud-2.svg",
      },
      {
        svg: "git.svg",
      },
    ],
    social_networks: [
      {
        icon: "github",
        url: "https://github.com/victorgalvez56",
        color: "",
        label: "",
      },
      {
        icon: "linkedin",
        url: "https://www.linkedin.com/in/v%C3%ADctor-galvez-260910177/",
        color: "primary",
        label: "",
      },
      {
        icon: "file-pdf-box",
        url: "/CV-+Victor+Galvez.pdf",
        color: "primary",
        label: "Descargar CV",
      },
    ],
    currentItem: "tab-Web",
    items: ["Web", "Shopping", "Videos", "Images", "asd", "asdasd"],
    more: ["News", "Maps", "Books", "Flights", "Apps"],
    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
  }),
  created() {
    this.language = this.$i18n.locale;
    this.dark = true;
  },
  methods: {
    addItem(item) {
      const removed = this.items.splice(0, 1);
      this.items.push(...this.more.splice(this.more.indexOf(item), 1));
      this.more.push(...removed);
      this.$nextTick(() => {
        this.currentItem = "tab-" + item;
      });
    },
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
    },
  },
};
</script>

<style>
.image {
  background: url("~static/bg.jpg");
  background-position: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  height: 100%;
}

.float:hover {
  text-decoration: none;
  color: black;
  background-color: #25d366;
}

.my-float {
  margin-top: 16px;
}
.padding-g {
  padding: 0 15px 15px 0;
}
</style>
