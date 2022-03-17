<template>
  <h1 class="my-5 text-center">Ingreso de Usuarios</h1>
  <form @submit.prevent="procesarFormulario">
        <input 
            type="email" 
            placeholder="Ingrese su email"
            class="form-control my-2"
            v-model.trim="email"
        >
        <input 
            type="password" 
            placeholder="Ingrese su contraseña"
            class="form-control my-2"
            v-model.trim="pass1"
        >
        <div class="d-grid gap-2">
            <button 
            type="submit"
            class="btn btn-dark btn-block my-3"
            :disabled="bloquear"
            >
                Ingresar
            </button>
        </div>       
  </form>
</template>

<script>
import { mapActions } from 'vuex'
export default {
    data() {
        return {
            email: '',
            pass1: '',
        }
    },
    computed: {
        bloquear(){
            if(!this.email.includes('@')){
                return true
            }
            if(this.pass1.length > 5){
                return false
            }
            return true
        }
    },
    methods: {
        ...mapActions(['ingresoUsuario']),
        procesarFormulario(){
            this.ingresoUsuario({email: this.email, password: this.pass1})
            this.email = '';
            this.pass1 = '';
        }
    }
}
</script>