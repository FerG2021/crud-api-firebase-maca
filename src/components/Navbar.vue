<template>
  <div class="navbar navbar-dark bg-dark">
      <router-link to="/" class="navbar-brand">
          Lista de tareas
      </router-link>
      <div class="d-flex">
          <!-- Boton tareas -->
          <router-link 
            class="btn btn-dark" 
            to="/"
            v-if="usuarioAutenticado"
            >
            Tareas
          </router-link>          

          <!-- Boton registrar -->
          <router-link 
            class="btn btn-dark" 
            to="/registro"
            v-if="!usuarioAutenticado"
            >
            Registrar
          </router-link>

          <!-- Boton ingresar -->
          <router-link 
            class="btn btn-dark" 
            to="/ingreso"
            v-if="!usuarioAutenticado"
            >
            Ingresar
          </router-link>

          <!-- Boton cerrar sesion -->
          <button
            class="btn btn-dark"
            v-if="usuarioAutenticado"
            @click="cerrarSesion"
          >
            Cerrar Sesión
          </button>
      </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  computed:{
    ...mapGetters(['usuarioAutenticado'])
  },
  methods: {
    ...mapActions(['cerrarSesion'])
  }
}
</script>

