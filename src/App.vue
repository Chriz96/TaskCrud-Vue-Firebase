<template>
  <Navbar />
 
  <div class="container">
    <router-view/>
  </div>
</template>

<script>
import {mapActions} from 'vuex'
import Navbar from '../src/components/Navbar'
export default {
  components:{
    Navbar
  },
  methods:{
    ...mapActions(['cargarBDTareas'])
  },
    created(){
    this.cargarBDTareas()
  }
}
</script>
