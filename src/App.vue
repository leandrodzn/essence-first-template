<template>
  <div class="position-relative text-center text-white">
    <img
      :src="imagenPrincipal"
      class="img-fluid w-100"
      style="filter: brightness(0.5)"
    />
    <div
      class="principal position-absolute top-50 start-50 translate-middle text-center"
    >
      <h1>{{ nombreNovia }} y {{ nombreNovio }}</h1>
      <h2>Nos casamos</h2>
    </div>
  </div>

  <nav class="py-3" style="background: #6f724a">
    <ul class="navegacion nav d-flex justify-content-evenly">
      <li class="nav-item" v-for="(seccion, index) in secciones" :key="index">
        <a class="nav-link text-white" :href="seccion.enlace">{{
          seccion.nombre
        }}</a>
      </li>
    </ul>
  </nav>

  <section id="nosotros" class="text-center">
    <div class="position-relative text-center text-white">
      <img :src="imagenNosotros" class="img-fluid w-100" />
      <div
        class="container position-absolute top-50 start-50 translate-middle text-center"
      >
        <div class="contador row px-4 py-5" style="background: #6f724a96">
          <div class="col-12 justify-content-center" md="12">
            <div class="container">
              <h1>{{ fechaFormateada }}</h1>
              <div class="row">
                <div class="col-4">
                  <h2>{{ tiempoRestante.dias }} días</h2>
                </div>
                <div class="col-4">
                  <h2>{{ tiempoRestante.horas }} horas</h2>
                </div>
                <div class="col-4">
                  <h2>{{ tiempoRestante.minutos }} minutos</h2>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="nosotros row my-4 d-flex justify-content-between">
          <div class="col-5 px-4 py-5" style="background: #ffffffcf">
            <h1>{{ nombreNovia }}</h1>
            <h2>La novia</h2>
            <p>{{ descripcionNovia }}</p>
          </div>
          <div class="col-5 px-4 py-5" style="background: #ffffffcf">
            <h1>{{ nombreNovio }}</h1>
            <h2>El novio</h2>
            <p>{{ descripcionNovio }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
  <section id="ubicacion" class="ubicacion">
    <div class="row py-4">
      <h1>Celebración religiosa</h1>
    </div>
    <div class="row">
      <div class="col-6" style="background: #6f724a96; padding: 5rem">
        <h2>{{ nombreLugarRel }}</h2>
        <h3>{{ fechaRel.hora }}:00 hrs</h3>
        <p>{{ descripcionLugarRel }}</p>
      </div>
      <div class="col-6 position-relative text-center text-white">
        <img
          :src="imagenUbicacion"
          class="img-fluid w-100"
          style="opacity: 57%"
        />
        <button
          class="btn position-absolute top-50 start-50 translate-middle text-center"
          style="background-color: #6f724a; color: white"
        >
          Ver ubicación
        </button>
      </div>
    </div>
    <div class="row py-4">
      <h1>Celebración social</h1>
    </div>
    <div class="row">
      <div class="col-6 position-relative text-center text-white">
        <img :src="imagenUbicacion2" class="img-fluid w-100" />
      </div>
      <div class="col-6" style="background: #6f724a96; padding: 5rem">
        <h2>{{ nombreLugarSoc }}</h2>
        <h3>{{ fechaSoc.hora }}:00 hrs</h3>
        <p>{{ descripcionLugarSoc }}</p>
      </div>
    </div>
    <div class="row py-4">
      <h1>Itinerario</h1>
    </div>
    <div class="row itinerario">
      <div class="row pb-5" v-for="(evento, index) in itinerario" :key="index">
        <div class="col-6 text-end">
          <img :src="evento.imagen" style="width: 9rem" />
        </div>
        <div class="col-6">
          <h1>{{ evento.evento }}</h1>
          <h2>{{ evento.horaInicio }} - {{ evento.horaFin }}</h2>
          <p>{{ evento.descripcion }}</p>
        </div>
      </div>
    </div>
    <div class="row position-relative text-center text-white">
      <img
        :src="imagenVestimenta"
        class="img-fluid w-100"
        style="filter: brightness(0.5)"
      />
      <div
        class="vestimenta container position-absolute top-50 start-50 translate-middle text-center"
      >
        <h1 class="text-white">Código de vestimenta</h1>
        <h2 class="text-white">{{ vestimenta }}</h2>
        <img :src="vestimenta1" style="width: 8rem" />
        <img :src="vestimenta2" style="width: 8rem" />
      </div>
    </div>
  </section>
  <section id="galeria" style="background: #6f724a7d">
    <div class="galeria row py-4 text-center">
      <h1>Galería</h1>
    </div>
    <div class="d-flex align-items-center justify-content-center">
      <div class="col-8">
        <vueper-slides
          class="no-shadow"
          :visible-slides="3"
          :gap="3"
          :slide-ratio="1 / 4"
          :dragging-distance="100"
        >
          <vueper-slide v-for="i in galeria" :key="i" :image="i.toString()" />
        </vueper-slides>
      </div>
    </div>
  </section>
  <section id="mesaregalos">
    <div class="mesa-regalos text-center py-4">
      <h1>Mesa de regalos</h1>
    </div>
    <div class="row">
      <div
        class="col-6 d-flex justify-content-center"
        style="background-color: #6f724a"
      >
        <img :src="imagenMesaRegalos" class="img-responsive" />
      </div>
      <div
        class="codigo-mesa col-6 d-flex flex-column justify-content-center align-items-center text-center text-white"
        style="background: #b2b4a0"
      >
        <h1>Código</h1>
        <h2>{{ codigoMesa }}</h2>
      </div>
    </div>
  </section>
  <section id="confirmacion">
    <div class="row position-relative text-center text-white">
      <img :src="imagenConfirmacion" class="img-fluid w-100" />
      <div
        class="position-absolute top-50 start-50 translate-middle text-center"
      >
        <div
          class="confirmacion container d-flex flex-column justify-content-center align-items-center"
          style="background: #ffffffcf; padding: 2rem"
        >
          <h1 style="color: #6f724a" class="pb-4">Confirma tu asistencia</h1>
          <h2 style="color: #6f724a" class="pb-4">
            Ingresa tu código de invitado para confirmar tu asistencia
          </h2>
          <input
            type="text"
            id="inputTexto"
            class="form-control w-50 p-3"
            placeholder="Código"
            v-model="codigoInvitado"
            style="background: #6f724a7d"
          />
          <button
            class="btn text-center m-4 px-5"
            style="background-color: #6f724a; color: white"
          >
            Enviar
          </button>
        </div>
      </div>
    </div>
    <div class="agradecimiento text-center py-5">
      <h1>Tu presencia es sumamente importante. <br />¡Gracias!</h1>
    </div>
  </section>
  <footer>
    <div style="background-color: #6f724a" class="p-4">
      <p style="color: white">
        © 2023. All rights reserverd. Powered by <b>Essence Creatives</b>.
      </p>
    </div>
  </footer>
</template>

<script>
import { VueperSlides, VueperSlide } from "vueperslides";
export default {
  data() {
    return {
      imagenPrincipal: "/assets/imagenPrincipal.png",
      imagenNosotros: "/assets/imagenNosotros.png",
      imagenUbicacion: "/assets/imagenUbicacion.png",
      imagenUbicacion2: "/assets/imagenUbicacion2.png",
      imagenVestimenta: "/assets/imagenVestimenta.png",
      imagenMesaRegalos: "/assets/imagenMesaRegalos.png",
      imagenConfirmacion: "/assets/imagenConfirmacion.png",
      vestimenta1: "/assets/vestimenta1.png",
      vestimenta2: "/assets/vestimenta2.png",
      codigoMesa: 688996,
      codigoInvitado: "",
      galeria: {
        imagen1: "/assets/galeria1.png",
        imagen2: "/assets/galeria2.png",
        imagen3: "/assets/galeria3.png",
        imagen4: "/assets/galeria4.png",
      },
      nombreNovia: "Carmen",
      descripcionNovia:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
      nombreNovio: "Alejandro",
      descripcionNovio:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
      nombreLugarRel: "Parroquia de San Francisco",
      descripcionLugarRel:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
      fechaRel: {
        dia: 25,
        mes: 12,
        anio: 2024,
        hora: 19,
      },
      nombreLugarSoc: "Hacienda Los Reyes Tizimín",
      descripcionLugarSoc:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
      fechaSoc: {
        dia: 25,
        mes: 12,
        anio: 2024,
        hora: 21,
      },
      itinerario: [
        {
          evento: "Recepción",
          horaInicio: "21:30",
          horaFin: "23:00",
          descripcion: "Comparte con nosotros este momento",
          imagen: "/assets/evento1.png",
        },
        {
          evento: "Cena",
          horaInicio: "22:00",
          horaFin: "23:00",
          descripcion: "Cenar juntos hace esta noche especial",
          imagen: "/assets/evento2.png",
        },
        {
          evento: "Fiesta",
          horaInicio: "23:00",
          horaFin: "03:00",
          descripcion: "¡Hey! Comienza la diversión",
          imagen: "/assets/evento3.png",
        },
      ],
      vestimenta: "Formal",
      fechaFormateada: "",
      tiempoRestante: {
        dias: 0,
        horas: 0,
        minutos: 0,
      },
      secciones: [
        { nombre: "Nosotros", enlace: "#nosotros" },
        { nombre: "Ubicación", enlace: "#ubicacion" },
        { nombre: "Galería", enlace: "#galeria" },
        { nombre: "Mesa de regalos", enlace: "#mesaregalos" },
        { nombre: "Confirmación", enlace: "#confirmacion" },
      ],
    };
  },
  mounted() {
    this.fechaFormateada = this.formatearFecha();
    this.tiempoRestante = this.calcularTiempoRestate();
    setInterval(this.calcularTiempoRestante, 1000);
  },
  methods: {
    formatearFecha() {
      const fecha = new Date();
      fecha.setFullYear(
        this.fechaRel.anio,
        this.fechaRel.mes - 1,
        this.fechaRel.dia
      );
      const opciones = { year: "numeric", month: "long", day: "numeric" };
      return fecha.toLocaleDateString("es-ES", opciones);
    },
    calcularTiempoRestate() {
      const fecha = new Date();
      fecha.setFullYear(
        this.fechaRel.anio,
        this.fechaRel.mes - 1,
        this.fechaRel.dia
      );
      fecha.setHours(this.fechaRel.hora, 0, 0);

      const fechaActual = new Date();

      const diferencia = fecha - fechaActual;

      const dias = Math.floor(diferencia / (1000 * 60 * 60 * 24));
      const horas = Math.floor(
        (diferencia % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      const minutos = Math.floor((diferencia % (1000 * 60 * 60)) / (1000 * 60));

      return { dias: dias, horas: horas, minutos: minutos };
    },
  },
  components: {
    VueperSlide,
    VueperSlides,
  },
};
</script>

<style>
.principal h1 {
  font-family: Alex Brush;
  font-size: 8rem;
}
.principal h2 {
  font-family: Arima;
  font-size: 6rem;
  font-weight: 100;
}
.navegacion a {
  font-family: Arima;
  font-size: 2rem;
}
input::placeholder {
  color: #ff5733;
  opacity: 1;
}
.img-responsive {
  max-width: 100%;
  height: auto;
  object-fit: cover;
}
.contador h1 {
  font-family: Alex Brush;
  font-size: 6rem;
}
.contador h2 {
  font-family: Arima;
  font-size: 3rem;
}
.nosotros h1 {
  color: #6f724a;
  font-family: Alex Brush;
  font-size: 7rem;
}
.nosotros h2 {
  color: black;
  font-family: Arima;
  font-size: 3rem;
}
.nosotros p {
  color: #6f724a;
  font-family: Arima;
  font-size: 1.5rem;
}
.ubicacion h1 {
  padding-top: 2rem;
  color: #6f724a;
  text-align: center;
  font-family: Alex Brush;
  font-size: 6rem;
}
.ubicacion h2 {
  color: #6f724a;
  font-family: Arima;
  font-size: 5rem;
}
.ubicacion h3 {
  color: white;
  font-family: Arima;
  font-size: 3rem;
}
.ubicacion p {
  color: white;
  font-family: Arima;
  font-size: 1.5rem;
}
.itinerario h1 {
  color: #6f724a;
  font-family: Arima;
  font-size: 2rem;
  text-align: start;
  font-weight: 700;
}
.itinerario h2 {
  color: #6f724a;
  font-size: 2rem;
  font-weight: 500;
}
.itinerario p {
  color: #6f724a;
  font-size: 2rem;
  font-weight: 300;
}
.vestimenta h1 {
  font-size: 6rem;
}
.vestimenta h2 {
  font-size: 4rem;
  font-weight: 200;
}
.galeria h1 {
  font-family: Alex Brush;
  font-size: 6rem;
  color: #6f724a;
}
.mesa-regalos h1 {
  font-family: Alex Brush;
  color: #6f724a;
  font-size: 6rem;
}

.codigo-mesa h1 {
  font-family: Arima;
  font-size: 3rem;
  font-weight: 500;
}

.codigo-mesa h2 {
  font-family: Arima;
  font-size: 3rem;
  font-weight: 300;
}

.confirmacion h1 {
  font-family: Alex Brush;
  font-size: 6rem;
  color: #6f724a;
}
.confirmacion h2 {
  font-family: Arima;
  font-size: 2.5rem;
  font-weight: 500;
}
.agradecimiento h1 {
  font-family: Alex Brush;
  color: #6f724a;
  font-size: 6rem;
}
footer {
  font-family: Montserrat;
  font-size: 1.5rem;
}
</style>
