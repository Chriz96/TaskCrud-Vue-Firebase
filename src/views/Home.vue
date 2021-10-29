<template>
<form @submit.prevent="procesarFormulario">
 <Input :tarea="tarea"/>

</form>
 <ListaTareas />
<hr>
</template>

<script>
import Input from '../components/Input'
import ListaTareas from '../components/ListaTareas'
import {mapActions} from 'vuex'
const shortid = require('shortid');

export default {
  name: 'Home',
  components: {
    Input,
    ListaTareas
  },
  data() {
    return {
      tarea:{
        id:'',
        nombre:'',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
  methods:{
    ...mapActions(['setTareas','cargarBDTareas']),

    procesarFormulario(){
      if(this.tarea.nombre.trim() === ""){
        return
      }
      this.tarea.id = shortid.generate()
      this.setTareas(this.tarea)

      this.tarea = 
      {
        id:'',
        nombre:'',
        categorias: [],
        estado: '',
        numero: 0
      }
    }
  },
    created(){
    this.cargarBDTareas()
  }

}
</script>
