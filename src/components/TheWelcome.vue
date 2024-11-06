<script setup>
import { ref } from 'vue'

defineProps({
  msg: {
    type: String,
    required: true,
  },
})

const weShouldRespect = ref(true) 
const showAnswer = ref(false);

const msgVegan = ref("Félicitations, vous êtes d'accord avec les véganes ! Plus qu'à aligner vos actes avec vos valeurs en arrêtant d'utiliser les autres animaux contre leur volonté : ")
const msgNonVegan = ref("Félicitations, vous êtes une personne sans valeurs de justice ou de respect, fermez ce site immédiatement.")

function onYesClick() {
  console.log("YES")
  weShouldRespect.value = true
  showAnswer.value = true
}

function onNoClick() {
  console.log("NO")
  weShouldRespect.value = false
  showAnswer.value = true
}
</script>

<template>
  <div class="greetings">
    <h2>{{ msg }}</h2>
    <button @click="onYesClick">Oui, bien sûr</button>
    <button @click="onNoClick">Non</button>
    <br />
    <br />
    <div v-if=showAnswer>
      <h4>{{ weShouldRespect ? msgVegan : msgNonVegan }}</h4>
      <a href="https://vegan-pratique.fr/" v-if="weShouldRespect">Vegan Pratique</a>
    </div>
    <h3 v-else>Suspense ...</h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: right;
  }
}
</style>
