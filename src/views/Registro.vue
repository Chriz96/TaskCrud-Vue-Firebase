<template>
  <h1 my-5>Create Account</h1>
    <form @submit.prevent="procesarFormulario()">
        <label :style="[emailAtSign? {color: 'green'}: {color:'red'}]">* Enter valid email.</label> <br>
        <label :style="[passwordLength ? {color: 'green'}: {color:'red'}]">* The password must be longer than 5 characters.</label><br>
        <label :style="[passwordMatch ? {color: 'green'}: {color:'red'}]">* Both passwords must match.</label>

        <input 
        type="email" 
        placeholder="email"
        class="form-control my-2"
        v-model.trim="email">
        <input 
        type="password" 
        placeholder="password"
        class="form-control my-2"
        v-model.trim="pass1"
        >
        <input 
        type="password" 
        placeholder="password"
        class="form-control my-2"
        v-model.trim="pass2">
        <button 
        type="submit"
        class="btn btn-primary btn-block"
        :disabled="bloquear" >
        Register</button>
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
computed : {
    bloquear(){
        if(!this.email.includes('@')){
        return true
         }
         if(this.pass1.length > 5 && this.pass1 === this.pass2){
        return false   
         }
         return true
    },
    emailAtSign(){
        if(this.email.includes('@')){
        return true
         }
        return false
    },
    passwordMatch(){
        if(this.pass1 === this.pass2){
        return true
        }
        return false
    },
    passwordLength(){
        if(this.pass1.length > 5){
        return true   
        }
        return false
        }
},
methods:{
    ...mapActions(['registrarUsuario']),
    procesarFormulario(){
        this.registrarUsuario({
        email:this.email,
        password:this.pass1
        }) 
        this.email = '',
        this.pass1 = '',
        this.pass2 = ''
    }
}

}
</script>
