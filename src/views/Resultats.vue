<template>
  <div id="questionnaire">
    <h3>Bienvenue {{prenom}} {{nom}} de la société {{societe}}</h3>
    <div class="results">
      <div v-for="(res, index) in results" class="resultat" :key="index">
        <span class="question">{{res.question.question}}</span>&nbsp;
        <span class="reponse">{{res.choice}}</span>&nbsp;
        <span v-if="res.choice !== res.question.bonneReponse" class="loose">Perdu ! La bonne réponse était : {{res.question.bonneReponse}}</span>
      </div>
      <span>Score {{score}}/{{results.length}}</span>
    </div>
  </div>
</template>

<script>

  export default {
    name: "Resultats",
    data() {
      return {
        nom: this.$route.query.nom,
        prenom: this.$route.query.prenom,
        societe: this.$route.query.societe,
        results: this.$route.query.results,
        score: this.$route.query.score
      }
    },
    mounted() {

    },
    methods: {}
  }
</script>

<style scoped>
  #questionnaire {
    height: 100%;
    display: grid;
    grid-template-columns: 15% 35% 35% 15%;
    grid-template-rows: 15% 35% 35% 15%;
    background-color: lightblue;
  }

  h3 {
    grid-row: 1/2;
    grid-column: 1/4;
  }

  .results {
    background-color: white;
    border-radius: 20px;
    grid-row: 2/4;
    grid-column: 2/4;
  }

  .loose {
    color: red;
    font-weight: bold;
  }
</style>