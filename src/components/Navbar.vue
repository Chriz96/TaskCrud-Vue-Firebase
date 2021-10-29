<template>
   <div class="navbar navbar-dark bg-dark">
       <router-link to="/" class="navbar-brand">
           Forms
       </router-link>
    <div class="d-flex">
        <router-link 
        class="btn btn-dark" 
        to="/"
        v-if="usuarioAutenticado"
        > 
            Tasks
        </router-link>

        <router-link 
        class="btn btn-dark" 
        to="/registro"
        v-if="!usuarioAutenticado"
        > 
            Register
        </router-link>

        <router-link 
        class="btn btn-dark" 
        to="/ingreso"
        v-if="!usuarioAutenticado"
        > 
            Sign In
        </router-link>

        <button
            class="btn btn-dark"
            v-if="usuarioAutenticado"
            @click="cerrarSesion"
        >
            Sign Off
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
