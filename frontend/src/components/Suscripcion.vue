<template>
  <div class="suscripcion">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-6">
          <h4>{{ suscripcion.titulo }}</h4>
          <p class="text-muted">
            {{ suscripcion.subtitulo }}
          </p>
          <form @submit.prevent="suscribirse">
            <input type="email" placeholder="usuario@gmail.com" name="email" />
            <input type="submit" value="Suscribirse" />
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2';
export default {
  name: "Suscripcion",
  methods: {
    suscribirse() {
      const Toast = Swal.mixin({
        toast: true,
        position: "top-end",
        showConfirmButton: false,
        timer: 3000,
        timerProgressBar: true,
        didOpen: (toast) => {
          toast.addEventListener("mouseenter", Swal.stopTimer);
          toast.addEventListener("mouseleave", Swal.resumeTimer);
        },
      });

      Toast.fire({
        icon: "info",
        title: "Estamos trabajando en esta funcionalidad",
      });
    },
  },
  props: {
    suscripcion: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.suscripcion {
  padding: 50px 0;
  background: #f3f5fa;
  text-align: center;
  font-size: 15px;
  color: #444444;
}
.suscripcion h4 {
  font-size: 24px;
  margin: 0 0 20px 0;
  padding: 0;
  line-height: 1;
  font-weight: 600;
  color: var(--secundario);
}
.suscripcion form {
  margin-top: 30px;
  background: #fff;
  padding: 6px 10px;
  position: relative;
  border-radius: 50px;
  box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.06);
  text-align: left;
}
.suscripcion form input[type="email"] {
  border: 0;
  padding: 4px 8px;
  width: calc(100% - 100px);
}
.suscripcion form input[type="submit"] {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  border: 0;
  background: none;
  font-size: 16px;
  padding: 0 20px;
  background: var(--primario);
  color: #fff;
  transition: 0.3s;
  border-radius: 50px;
  box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.1);
}
.suscripcion form input[type="submit"]:hover {
  background: #0ea38f;
}
</style>