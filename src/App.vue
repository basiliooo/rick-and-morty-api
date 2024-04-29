<script setup>
import {ref} from 'vue'

let num = ref(0)

</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark border-bottom border-body">
    <div class="container-fluid ">
      <router-link class="navbar-brand" to="/">Rick And Morty</router-link>
    </div>
  </nav>

  <div class="main">
    <router-view></router-view>
  </div>

</template>

<style>
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50px;
  }
  </style>