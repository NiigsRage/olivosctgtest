<template>
  <v-app ligth>
    <v-app-bar app color="#ffffff" dark elevation="3" fixed>
      <v-btn to="/" text>
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="images/LOGO LOS OLIVOS Version polocromia-01.png"
          transition="scale-transition"
          width="150"
          to="/"
        />
      </v-btn>
      <v-img
        alt="Vuetify Name"
        class="shrink mt-1 hidden-sm-and-down"
        contain
        min-width="100"
        width="100"
      />
      <v-spacer></v-spacer>
      <div class="hidden-sm-and-down">
        <v-btn
          v-for="link in links"
          :key="link.id"
          :to="link.link"
          text
          color="#008856"
          style="font-weight: bold"
        >{{link.label}}
        </v-btn>
      </div>
      <div class="hidden-md-and-up">
        <v-menu transition="slide-y-transition">
          <template v-slot:activator="{ on }">
            <v-btn
              dark
              icon
              v-on="on"
              color="black"
            >
              <v-icon color="#008856">mdi-dots-vertical</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item v-for="link in links" :key="link.id">
              <v-btn color="#008856" text style="font-weight: bold">{{ link.label }}</v-btn>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>
    </v-app-bar>
    <div class="social">
      <ul>
        <li><a href="https://www.facebook.com/Olivos.Ctg/" target="_blank" class="icon-facebook"><img
          src="/images/face.png"
          alt="facebook"></a></li>
        <li><a href="https://www.instagram.com/olivos.ctg/" target="_blank" class="icon-twitter"><img
          src="/images/ig.png"
          alt="instagram"></a>
        <li><a href="https://api.whatsapp.com/send?phone=+573008131043" target="_blank" class="icon-googleplus"><img
          src="/images/wha.png"
          alt="whatsapp"></a></li>
        <li><a href="https://www.youtube.com/channel/UC8_DB9iEH5HhFh0xy-cXTIA" target="_blank" class="icon-youtube"><img
          src="/images/youtube.png"
          alt="youtube"></a>
        </li>
      </ul>
    </div>

    <nuxt/>

    <Footer/>
  </v-app>
</template>

<script>
  import Footer from "../components/footer";

  export default {
    components: {Footer},
    data() {
      return {
        links: [
          {label: 'Obituarios', link: '#obituarios'},
          {label: 'Planes', link: '#planes'},
          {label: 'Necesidad inmediata'},
          {label: 'Servicios adicionales'},
          {label: 'Tienda'},
          {label: 'Blog'},
          {label: 'Nosotros'}
        ],
      }
    },

  }
</script>

<style>
  .social {
    position: fixed;
    left: -35px;
    top: 200px;
    z-index: 2000;
  }

  .social ul {
    list-style: none;
  }

  .social ul li a {
    display: inline-block;
    color: #fff;
    background: #000;
    padding: 10px 15px;
    text-decoration: none;
    -webkit-transition: all 500ms ease;
    -o-transition: all 500ms ease;
    transition: all 500ms ease;
  }

  .social ul li .icon-facebook {
    background: #008856;
    margin-bottom: 3px;
  }

  .icon-facebook > img {
    width: 20px;
  }

  .icon-twitter > img {
    width: 20px;
  }

  .icon-googleplus > img {
    width: 20px;
  }

  .social ul li a {
    border-radius: 0px 118px 118px 0px;
  }

  .social ul li .icon-twitter {
    background: #008856;
    margin-bottom: 3px;
  }

  .icon-youtube > img {
    width: 20px;
  }

  .social ul li .icon-youtube {
    background: #008856;
    margin-top: 3px;
  }

  .social ul li .icon-googleplus {
    background: #008856;
  }


  .social ul li a:hover {
    padding: 10px 30px;
  }
</style>
