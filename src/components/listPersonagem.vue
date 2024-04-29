<script setup>
const personagem = defineProps(["name", "url", "status", "species", "gender", "location", "episode"])
const personagemId = personagem.url.split('/')[5]
const imageUrl = "https://rickandmortyapi.com/api/character/avatar/" + personagemId + ".jpeg" 

let colorStatus = ''

switch (personagem.status) {
    case "Alive":
        colorStatus = "darkgreen"
        break;
    case "Dead":
        colorStatus = "darkred"
        break;
    default:
        colorStatus = "darkblue"
        break;
}

</script>

<template>
<div class="card text-bg-dark border-light mb-3" style="max-width: 540px;">
  <div class="row g-0">
    <div class="col-md-4">
      <img :src="imageUrl" class="img-fluid rounded-start" alt="...">
    </div>
    <div class="col-md-8">
      <div class="card-body">
        <h5 class="card-title"><strong>Nome: </strong>{{personagem.name}}</h5>
        <p class="text-start small status"><strong>Status: </strong><strong :style="{ color: colorStatus}"> {{personagem.status}}</strong></p>
        <p class="text-start small"><strong>Espécie: </strong>{{personagem.species}}</p>
        <p class="text-start small"><strong>Gênero: </strong>{{personagem.gender}}</p>
        <p class="text-start small"><strong>Local: </strong>{{personagem.location}}</p>
        <p class="text-start small">Aparece em: <strong>{{personagem.episode}}</strong> episódios.</p>
      </div>
    </div>
  </div>
</div>
</template>
