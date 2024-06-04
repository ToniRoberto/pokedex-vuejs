<script setup>
    //importações
    import { onMounted, ref } from "vue";

    //variavel para exibir carregamento
    let carregamento = ref(true);

    //vetor pokemom
    let vetor = ref([]);

    //variavel para armazenar texto filtro
    let textoFiltro = ref('');

    //oMounted
    onMounted(async() =>{
        for (let indice = 152; indice <= 251; indice++){
            let requisicao = await fetch('https://pokeapi.co/api/v2/pokemon/'+indice)
            let pokemom = await requisicao.json();
            vetor.value.push(pokemom);
        }

        carregamento.value = false;
    });
    //função para filtrar
    function filtrar(){
        return vetor.value.filter(obj => obj.name.toLowerCase().includes(textoFiltro.value.toLowerCase()));
    }
</script>
<template>
    <h1>2ª Geração</h1>

    <div class="carregamento" v-if="carregamento">
        <img src="../complementos/pokeball.gif">
    </div>

    <main class="container" v-if="!carregamento">
        <!--FILTRAGEM-->
        <div class="row">
            <div class="col-12">
                <input type="text" v-model="textoFiltro" placeholder="Digite o nome de um Pokémon" class="form-control pesquisa">

                <p v-if="filtrar().length == 0">Não foi Encontrado nenhuma Pokémon!</p>
                <p v-else-if="filtrar().length == 1">Foi Encontrado apenas um Pokémon!</p>
                <p v-else>Foram encontrados {{ filtrar().length }} Pokémons!</p>
            </div>
        </div>

        <!--LISTAGEM-->
        <div class="row">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="v in filtrar()">
                <div class="card" :class="v.types[0].type.name">
                    <img :src="v.sprites.other.home.front_default">
                    <p>{{ v.name }}</p>
                </div>
            </div>
        </div>
    </main>
</template>