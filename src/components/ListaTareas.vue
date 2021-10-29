<template>
<div class="table-responsive-lg mt-2"> 
    <table class="table table-dark">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Name</th>
      <th scope="col">Categories</th>
      <th scope="col">State</th>
      <th scope="col">Number</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="item in tareas" :key="item.id">
      <th scope="row">{{item.id}} </th>
      <td>{{item.nombre}}</td>
    <td>
        {{item.categorias.join(', ')}}
    </td> 

      <td>{{item.estado}}</td>
      <td>{{item.numero}}</td>
      <td>
          <button class="btn btn-danger btn-sm" @click="deleteTareas(item.id)">Remove</button>
          <router-link
          class="btn btn-warning ml-2 btn-sm"
          :to="{
              name:'Editar',
              params: {
                  id: item.id
              }
          }"> 
              Edit
          </router-link>

      </td>
    </tr>
  </tbody>
</table>
</div>

</template>

<script>
import {mapState,mapActions} from 'vuex'
export default {
    computed:{
        ...mapState(['tareas'])
    },
    methods:{
        ...mapActions(['deleteTareas'])
    }

}
</script>
