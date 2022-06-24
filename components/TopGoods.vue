<template>
  <v-card
    :loading="loading"
    max-width="23vw"
    style="margin-left: 1vw; margin-bottom: 2vh; margin-right: 1vw;"
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      />
    </template>

    <v-img
      height="35vh"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
    />

    <v-card-title>Вейп 1</v-card-title>

    <v-card-subtitle>
      Цена: 1800 р
    </v-card-subtitle>

    <v-divider class="mx-4" />

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="reserve"
      >
        Купить
      </v-btn>
    </v-card-actions>
  </v-card>
</template>
<script>

export default {
  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    }
  }
}
</script>
