<template>
  <v-content>

    <v-carousel
      cycle
      height="600"
      hide-delimiter-background
      hide-delimiters
      show-arrows
    >
      <v-carousel-item
        v-for="(slide, i) in slides"
        :key="i"

      >
        <v-parallax
          :src="colors[i]"
          height="600"
        >
          <v-row
            class="fill-height"
            align="center"
            justify="center"
          >
            <h1 class="display-3 img-title" style="font-family: 'Arimo', sans-serif !important; text-align: center;">
              {{ slide }}
              <br>
              <v-btn :to="links[i]" nuxt color="withe" style="font-weight: bold" outlined large>Conoce más</v-btn>
            </h1>

          </v-row>
        </v-parallax>
      </v-carousel-item>
    </v-carousel>
    <v-row class="s2" align="center" justify="center">
      <v-col>
        <h1 class="divider_1" style="font-family: 'Arimo', sans-serif !important; color: white">Trascendimos de la protección exequial
          a la protección familiar</h1>
      </v-col>
    </v-row>
    <!--Planes-->
    <div class="back_s1 d-flex align-center">
      <v-container>
        <v-row justify="center" class="mb-12">
          <h1 class="s2_title" id="planes">¡Descubre tu plan ideal!</h1>
          <carousel-3d autoplay :clickable="false" :controls-visible="true" :width="482" :space="400" :perspective="0"
                       :animationSpeed="700">
            <slide v-for="(images, i) in images_planes" :key="i" :index="i">
              <nuxt-link to="/inpire">
                <v-img :src="images.ruta" :alt="images.alt"></v-img>
                <p>Plan</p>
              </nuxt-link>
            </slide>
          </carousel-3d>
        </v-row>
      </v-container>
    </div>

    <svg style="margin-bottom: -8px; background-color: #fafafa;;" xmlns="http://www.w3.org/2000/svg"
         class="curve-container__curve curve-one" viewBox="0 0 1440 68" enable-background="new 0 0 1440 68">
      <path d="m1622.3 1937.7c0 0-410.7 169.1-913.4 75.5-502.7-93.6-977.7 56.3-977.7 56.3v440h1891.1v-571.8"
            fill="#f4f4f4" transform="translate(0-1977)"/>
    </svg>
    <div class="s3 d-flex align-center" id="obituarios">
      <v-container>
        <v-row class="ro mb-12" align="center"
               justify="center">
          <h1 class="s2_title mb-5">Obituarios</h1>
          <div class="owl-carousel">
            <template v-for="(obituarios, i) in obituarios_data">
              <div :key="obituarios.id" class="mb-1">
                <v-card
                  class="mx-auto"
                  max-width="380"
                >
                  <v-img
                    class="align-center justify-center fondo_obi"
                    height="200px"
                  >
                    <v-card-title class="text_title_h justify-center align-center">{{obituarios.nombre_ser_querido}}</v-card-title>
                  </v-img>

                  <v-card-subtitle class="pb-0">{{obituarios.fecha}}</v-card-subtitle>

                  <v-card-text class="text--primary">
                    <div><span class="font-weight-bold">Exequias: </span>{{obituarios.exequias}}</div>
                    <div><span class="font-weight-bold">Hora exequias: </span>{{obituarios.hora_exequias}}</div>
                    <div><span class="font-weight-bold">Inhumación: </span>{{obituarios.inhumacion}}</div>
                    <div><span class="font-weight-bold">Hora inhumación: </span>{{obituarios.hora_inhumacion}}</div>
                  </v-card-text>

                  <v-card-actions class="justify-center">
                    <v-btn
                      color="#008856"
                      depressed
                      class="font-weight-bold"
                      dark
                      small
                      block
                    >
                      enviar condolencia
                      <v-icon right>mdi-send</v-icon>
                    </v-btn>
                  </v-card-actions>
                  <v-card-actions class="justify-center">
                    <v-btn
                      color="#008856"
                      depressed
                      class="font-weight-bold text-truncate"
                      dark
                      small
                      block
                      @click="obituarios.estado = !obituarios.estado"
                    >
                      {{ obituarios.estado ? 'Ocultar condolencias' : 'Ver condolencias' }}
                      <v-icon right>{{ obituarios.estado ? 'mdi-arrow-up-bold' : ' mdi-arrow-down-bold' }}</v-icon>
                    </v-btn>
                  </v-card-actions>
                  <v-expand-transition>
                    <div v-show="obituarios.estado">
                      <v-divider/>
                      <v-card-text>
                        No hay condolencias.
                      </v-card-text>
                    </div>
                  </v-expand-transition>
                </v-card>
              </div>
            </template>
          </div>
        </v-row>
      </v-container>
    </div>

    <div class="s4">

      <v-parallax
        dark
        src="/images/fr.jpg"
        id="para"
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-container>
            <v-col class="testimonios text-center" cols="12">
              <h1 class="mb-4 text_testimonios">Testimonios</h1>
              <h4 class="subheading">Que dicen de nosotros</h4>
              <v-btn class="mt-5" outlined color="white">Ver más</v-btn>
            </v-col>
          </v-container>
        </v-row>
      </v-parallax>
    </div>


  </v-content>
</template>

<script>
  import axios from 'axios';

  export default {
    components: {},
    head: {
      title: 'Inicio'
    },
    data() {
      return {
        obituarios_data: [],
        colors: [
          '/images/1.jpg',
          '/images/2.jpg',
          '/images/3.jpg',
          '/images/4.jpg',
          '/images/5.jpg',
        ],
        slides: [
          'Necesidad inmediata',
          'Parque Jardín Los Olivos',
          'Tienda Olivos',
          'Acompañamiento',
          'Obituarios',
        ],
        links: [
          '/inspire'
        ],
        images_planes: [
          {ruta: '/images/planhuellitas.jpg', alt: 'plan huellitas'},
          {ruta: '/images/planfamiliar.jpg', alt: 'plan familiar'},
          {ruta: '/images/plan10.jpg', alt: 'plan 10'},
          {ruta: '/images/planunidos.jpg', alt: 'plan unidos'},
          {ruta: '/images/plansuperior.jpg', alt: 'plan superior'},
          {ruta: '/images/plan6mas1.jpg', alt: 'plan 6 mas 1'},
          {ruta: '/images/planfraternal.jpg', alt: 'plan fraternal'},
          {ruta: '/images/planunico.jpg', alt: 'plan unico'},
        ],
      }
    },
    methods: {
      async getObituarios() {
        try {
          let respose = await axios.get('https://www.api.losolivoscartagena.com/api/obituarios');
          this.obituarios_data = respose.data;
          let info;
          for (let i = 0; i < respose.data.length; i++) {
            info = i;
          }
          if (process.client) {
            $(document).ready(function () {
              $('.owl-carousel').owlCarousel({
                loop: true,
                margin: 10,
                //autoWidth: true,
                center: false,
                nav: false,
                autoplay: info >= 2,
                autoplayHoverPause: true,
                responsive: {
                  0: {
                    items: 1,
                    autoplay: true
                  },
                  600: {
                    items: info === 0 ? 1 : info === 1 ? 2 : 3
                  },

                  1400: {
                    items: info === 0 ? 1 : info === 1 ? 2 : 3
                  }
                }
              })
            });
          }
        } catch (error) {
          console.log(error)
        }
      }
    },
    mounted() {
      this.getObituarios();

    }
  }


</script>

<style>
  .img-title {
    color: white;
    font-weight: bold !important;
    text-shadow: 0px 0px 30px #008856;
  }


  .text_testimonios {
    font-size: 3rem;
  }

  .back_s1 {
    height: 650px;
  }

  .divider_1 {
    font-size: 2.5rem;
    text-align: center;
  }

  .testimonios {
    line-height: 25px;
  }

  .fondo_obi {
    background: linear-gradient(to top right, rgba(100,115,201,.33), rgba(25,32,72,.7)), url("/images/homenaje_title.jpg");
    background-size: cover;
  }

  .b {
    background-image: url("/images/VER.png");
    background-size: contain;
  }

  .s3 {
    background-color: #f4f4f4;
    height: 650px;
  }

  .s2 {
    background-image: radial-gradient(circle farthest-corner at 10% 20%, rgba(43, 194, 57, 1) 0%, rgba(149, 250, 113, 0.8) 90%);
    height: 110px;
  }

  .s2 > h1 {
    color: white;
    text-shadow: 0px 2px 6px #000000;
  }


  .s2_title {
    color: #008856 !important;
    font-size: 3rem;
    text-shadow: 0 3px 2px rgba(150, 150, 150, 1);
    text-align: center;
  }

  .text_title_h {
    color: white;
    font-size: 1.5rem;
    text-align: center;
    font-weight: bold;
  }

  @media only screen and (max-width: 415px) {
    .display-3 {
      font-size: 2rem !important;
    }

    .ro {
      margin-right: -12px;
      margin-left: -12px;
    }

    .s2_title {
      font-size: 3.2rem;
    }

    .divider_1 {
      font-size: 1.4rem;
      text-align: center;
    }
  }

  @media only screen and (min-width: 767px) and (max-width: 768px) {
    .divider_1 {
      font-size: 1.9rem;
    }
  }
</style>
