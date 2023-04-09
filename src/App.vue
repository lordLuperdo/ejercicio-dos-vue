<script setup>
import { ref,computed } from "vue"
import tarjetas from "./components/tarjetas.vue"
import loading from "./components/loading.vue"
import botonCambiar from "./components/botonCambiar.vue"
const posts = ref([])
const cargando =ref(true)


let nombre = ref("");
let primer = ref(0)
let segundo = ref(10)
const ponernombre = (title)=> {
nombre.value= title;
}

const bloquearboton = computed( ()=>{
  return primer.value === 0
}

)
const sumar= ()=> {
primer.value+=10
segundo.value+=10
}

const restar= ()=> {
  primer.value-=10
  segundo.value-=10
} 


  fetch("https://jsonplaceholder.typicode.com/posts")
  .then(res=>res.json())
  .then(data => posts.value = data)
  .finally( ()=>{
    cargando.value = false
  })
</script>

<template>
  <loading v-if="cargando"></loading>
  <div class="container mt3 text-center" v-else>
    <h1 class="mb-4 mt-4">app {{ nombre }}</h1>
   
    <botonCambiar 
    :inicio ="primer"
    :fin ="segundo"
    @bloquearboton = "bloquearboton"
    @sumar="sumar"
    @restar ="restar"
    class="mb-4" title="atras" title2="adelante">
    </botonCambiar>
    
    
    <tarjetas 
    v-for="post in posts.slice(primer,segundo)" 
    :key="post.id"
    :title="post.title"
    :texto="post.body"
    :id="post.id"
    @cambiarnombre = "ponernombre"
    class="mb-2"
    ></tarjetas>
  </div>

</template>