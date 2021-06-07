<template>
  <div>
    <b-container>
      <p>{{ joke.setup }}</p>

      <div class="accordion" role="tablist">
        <b-card no-body class="mb-1">
          <b-card-header header-tag="header" class="p-1" role="tab">
            <b-button block v-b-toggle.accordion-1 variant="outline-dark"
              >Toggle for punchline</b-button
            >
          </b-card-header>
          <b-collapse id="accordion-1" accordion="my-accordion" role="tabpanel">
            <b-card-body>
              <b-card-text>
                <p>{{ joke.punchline }}</p>
                </b-card-text>
            </b-card-body>
          </b-collapse>
        </b-card>
      </div>

      <b-button class="mt-3" variant="success" v-on:click="getJoke()">New joke</b-button>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Start",
  data() {
    return { joke: [] };
  },
  mounted() {
    this.getJoke();
  },
  methods: {
    getJoke() {
      axios
        .get("https://official-joke-api.appspot.com/random_joke")
        .then((res) => (this.joke = res.data));
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.accordion {
  width: 20em;
  margin: auto;
}
</style>
