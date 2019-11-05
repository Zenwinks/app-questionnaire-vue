<template>
  <div id="questionnaire">
    <h3>Bienvenue {{prenom}} {{nom}} de la société {{societe}}</h3>
    <div class="results">
      <div v-for="(res, index) in results" v-if="res.question" class="resultat" :key="index">
        <span class="question">{{res.question.question}}</span>&nbsp; <br>
        <span class="reponse">Votre réponse : <i>{{res.choice}}</i></span>&nbsp;
        <font-awesome-icon icon="check-square"></font-awesome-icon>
        <span v-if="res.choice !== res.question.bonneReponse" class="loose">Perdu ! La bonne réponse était : {{res.question.bonneReponse}}</span>
      </div>
      <span class="score">Score : {{score}}/{{results.length}}</span>
      <b-button block variant="primary" class="go-to-accueil" @click="navToAccueil"><b>Accueil</b>
      </b-button>
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
    methods: {
      navToAccueil() {
        this.$router.push({
          path: '/'
        })
      }
    }
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

  .resultat {
    margin: 20px 0 0 20px;
  }

  .question {
    font-weight: bold;
  }

  .loose {
    color: red;
    font-weight: bold;
  }

  .score {
    font-weight: bold;
    font-size: 30px;
    float: right;
    margin-right: 20px;
    margin-bottom: 10px;
  }
</style>