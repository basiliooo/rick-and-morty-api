<script setup>
import {ref} from 'vue'

let num = ref(0)

</script>

<template>
<nav class="navbar navbar-expand-lg navbar-dark bg-dark border-bottom border-body">
        <div class="container-fluid">
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link class="navbar-brand" to="/">Rick and Morty</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link class="nav-link" to="/about">Sobre</router-link>
                    </li>
                </ul>
            </div>
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
