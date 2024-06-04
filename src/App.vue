<script setup>
  //importando os elementos
  import { RouterLink, RouterView } from 'vue-router'

  //importando o bootstrap
  import 'bootstrap/dist/css/bootstrap.min.css'

  //importa estilo css
  import './componentes/estilo.css'

  //importar componente de navegação
  import BarraNavegacao from './componentes/BarraNavegacao.vue'
</script>

<template>
      <!--Barra Navegação-->
      <BarraNavegacao></BarraNavegacao>

      <!--Visualizar conteudo-->
      <RouterView />
</template>
