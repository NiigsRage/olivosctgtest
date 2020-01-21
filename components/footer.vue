<template>
  <v-content>
    <v-container>
      <v-row>
        <v-col cols="12" md="6" class="d-flex justify-center flex-wrap text-center font-weight-bold">
          <div style="height: 120px">
            <v-img src="/images/LOGO LOS OLIVOS Version polocromia-01.png" max-width="330"/>
          </div>
          <div class="direccion">
            <p>Dirección</p>
            <p>Carretera la Cordialidad Trv 54 #31-J27</p>
            <p>PBX: (5) 6535833</p>
            <p>Cartagena, Bolívar</p>
          </div>
          <div class="btn">

          </div>


        </v-col>
        <v-col cols="12" md="6" class="d-flex justify-center">
          <div class="form">
            <v-form v-model="valid" ref="form">
              <v-text-field label="Nombre y apellido" v-model="nombre_apellido" :rules="NombreApellidoRules"/>
              <v-text-field label="Correo" :rules="correoRules" v-model="correo"/>
              <v-text-field label="Teléfono" :rules="numeroRules" v-model="numero"/>
              <v-textarea label="Comentarios" v-model="comentarios"/>
              <v-checkbox label="Aceptar terminos y condiciones" class="" v-model="checkbox"
                          :rules="[v => !!v || 'Debes aceptar los terminos y condiciones']"/>

              <v-btn color="#008856" @click="SendEmail" :disabled="!valid" :loading="loadingbtn">Enviar</v-btn>
            </v-form>
          </div>
        </v-col>
        <v-col cols="12" md="6" class="d-flex justify-center text-center font-weight-bold">


        </v-col>
      </v-row>
    </v-container>
  </v-content>
</template>

<script>
  import axios from 'axios'
  import toastr from 'toastr'
  import 'toastr/build/toastr.css'

  toastr.options = {
    "positionClass": "toast-bottom-right",
    "progressBar": true,
  };

  export default {
    data: () => ({
      valid: false,
      loadingbtn: false,
      nombre_apellido: '',
      NombreApellidoRules: [
        v => !!v || 'El nombre y apellido es requerido'
      ],
      correo: '',
      correoRules: [
        v => !!v || 'El correo es requerido',
        v => /.+@.+\..+/.test(v) || 'Ingrese un correo valido',
      ],
      numero: '',
      numeroRules: [
        v => !!v || 'El numero es requerido',
      ],
      comentarios: '',
      checkbox: false,
    }),
    methods: {
      validate() {
        if (this.$refs.form.validate()) {
          this.valid = true;
        }
      },
      reset () {
        this.$refs.form.reset()
      },
     async SendEmail() {
        this.loadingbtn = true;
        try {
          if (this.validate()) {
            return;
          }
          let response = await axios.get('https://www.api.losolivoscartagena.com/api/email', {
            params: {
              'nombre_apellido': this.nombre_apellido,
              'correo': this.correo,
              'telefono': this.numero,
              'comentario': this.comentarios
            }
          });
          toastr.success('Gracias, hemos recibido sus datos');
          this.loadingbtn = false;
          this.reset();
          console.log(response)
        } catch (e) {
          this.loadingbtn = false;
        }
      }
    },
  }
</script>

<style scoped>
  .form {
    background: rgba(0, 136, 86, 0.05);
    width: 50%;
    padding: 20px;
    border-radius: 5px;
  }

  .direccion {
    color: #04040473;
    width: 100%;
  }

  .btn {
    border-radius: 5px;
    transition: transform 0.2s;
    background-image: url("/images/P Q R S.png");
    position: relative;
    height: 111px;
    width: 286px;
  }

  .btn:hover {
    transform: scale(1.1);
  }

  .c:disabled {
    background-color: red !important;
  }

  @media only screen and (max-width: 417px) {
    .form {
      width: 100%;
    }

    .direccion {
      margin-top: 50px;
    }
  }


</style>
