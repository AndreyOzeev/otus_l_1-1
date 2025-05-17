<script setup>
import {ref} from 'vue'

const title = 'Homework 2'

const users = ref([
  {id: 1, name: 'Иван', age: 25, hover: false},
  {id: 2, name: 'Мария', age: 30, hover: false},
  {id: 3, name: 'Петр', age: 22, hover: false},
])

const showAge = ref(false)
const showList = ref(true)

function toggleAge() {
  showAge.value = !showAge.value
}

function toggleList() {
  showList.value = !showList.value
}

function mouseOver(user) {
  user.hover = true
}

function mouseOut(user) {
  user.hover = false
}
</script>

<template>
  <h1>{{ title }}</h1>
  <button @click="toggleList">{{ showList ? 'Скрыть список' : 'Показать список' }}</button>
  <button @click="toggleAge">{{ showAge ? 'Скрыть возраст' : 'Показать возраст' }}</button>

  <ul class="list" v-if="showList">
    <li class="list__item" v-for="user in users" :key="user.id"
        @mouseover="mouseOver(user)"
        @mouseout="mouseOut(user)"
        :style="{ color: user.hover ? 'blue' : 'black' }"
    >
      {{ user.name }}
      <span v-if="showAge"> - {{ user.age }} лет</span>
    </li>
  </ul>
</template>

<style scoped lang="scss">
.list {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 10px;
  margin: 20px 0;
  padding-left: 0;

  list-style-type: none;
}

.read-the-docs {
  color: #888;
}
</style>
