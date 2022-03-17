<template>
  <h1 class="my-5 text-center">Registro de Usuarios</h1>
  <form @submit.prevent="procesarFormulario">
        <input 
            type="email" 
            placeholder="Email"
            class="form-control my-2"
            v-model.trim="email"
        >
        <input 
            type="password" 
            placeholder="Contraseña (mínimo 6 caracteres)"
            class="form-control my-2"
            v-model.trim="pass1"
        >
        <input 
            type="password" 
            placeholder="Confirmar contraseña"
            class="form-control my-2"
            v-model.trim="pass2"
        >
        <div class="d-grid gap-2">
            <button 
            type="submit"
            class="btn btn-dark btn-block my-3"
            :disabled="bloquear"
            >
                Registrar
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
            pass2: ''
        }
    },
    computed: {
        bloquear(){
            if(!this.email.includes('@')){
                return true
            }
            if(this.pass1.length > 5 && this.pass1 === this.pass2){
                return false
            }
            return true
        }
    },
    methods: {
        ...mapActions(['registrarUsuario']),
        procesarFormulario(){
            this.registrarUsuario({email: this.email, password: this.pass1})
            this.email = '';
            this.pass1 = '';
            this.pass2 = '';
        }
    }
}
</script>