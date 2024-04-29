<script setup>
import { onMounted, ref } from "vue";
import listPersonagem from "../components/listPersonagem.vue";

let personagens = ref([]);
const contador = ref(1);

const fetchPersonagens = () => {
  const url = `https://rickandmortyapi.com/api/character/?page=${contador.value}`;
  fetch(url)
    .then((response) => response.json())
    .then((response) => {
      personagens.value = response.results;
      console.log(personagens);
    });
};

onMounted(fetchPersonagens);

const nextPage = () => {
  if (contador.value < 42) {
  contador.value++;
    personagens.value = [];
  fetchPersonagens();
  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });
  }
};

const backPage = () => {
  if (contador.value > 1) {
    contador.value--;
    personagens.value = [];
    fetchPersonagens();
  }
};
</script>

<template>
  <main>
      <div class="p-4">
      <p class="text-center">{{ contador }} | 42</p>
      <div class="d-flex justify-content-center grid gap-3">
        <div @click="backPage">
          <button type="button" class="btn btn-dark bi bi-caret-left-fill seta">Voltar</button>
        </div>
        <div @click="nextPage">
          <button type="button" class="btn btn-dark bi bi-caret-right-fill seta">Próximo</button>
        </div>
      </div>
    </div>
    <div class="container-fluid">
      <div class="row mt-4 d-flex justify-content-center">
        <div class="col-md-8">
          <div class="card">
            <div class="card-body row">
              <listPersonagem
                v-for="personagem in personagens"
                :key="personagem.name"
                :name="personagem.name"
                :url="personagem.url"
                :status="personagem.status"
                :species="personagem.species"
                :gender="personagem.gender"
                :location="personagem.location.name"
                :episode="personagem.episode.length"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
