<template>
  <div>
    <h2 class="theme-title">Thème</h2>
    <div class="d-flex flex-column">
      <button
        class="btn btn-primary d-block"
        @click="montrerListe = !montrerListe"
      >
        {{ theme ? theme.titre : "Choisir un thème..." }}
      </button>
      <div class="btn-group-vertical btn-group-md" v-if="montrerListe">
        <button
          class="btn btn-secondary text-left"
          v-for="theme in listeTheme"
          :key="theme.id"
          @click="selectTheme(theme)"
        >
          {{ theme.titre }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ThemeSelect",
  props: ["listeTheme"],
  data: function() {
    return {
      theme: null,
      montrerListe: false
    };
  },
  methods: {
    selectTheme(theme) {
      this.theme = theme;
      this.montrerListe = false;
      this.$emit("select-theme", theme.id);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.theme-title {
  margin-right: 1rem;
}
</style>
