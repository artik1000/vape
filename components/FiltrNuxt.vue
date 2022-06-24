<template>
    <v-range-slider
      v-model="range"
      :max="max"
      :min="min"
    >
      <template #prepend>
        <v-text-field
          :value="range[0]"
          type="number"
          style="width: 60px;"
          @change="$set(range, 0, $event)"
        />
      </template>
      <template #append>
        <v-text-field
          :value="range[1]"
          type="number"
          style="width: 60px;"
          @change="$set(range, 1, $event)"
        />
      </template>
    </v-range-slider>
</template>
<script>
export default {
  data () {
    return {
      min: 100,
      max: 10000,
      range: [2000, 3000]
    }
  }
}
</script>
<style>
</style>
