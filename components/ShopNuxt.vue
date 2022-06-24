<template>
  <v-card class="poka">
    <v-card-title
      class="justify-center"
    >
      Фильтры
    </v-card-title>
    <v-col
      class="d-flex"
      style="width: 100%"
    >
      <v-select
        :items="items"
        label="Тип продукта"
      />
    </v-col>
    <v-col>
      <v-card-title
              class="justify-center"
      >
        Цена
      </v-card-title>
      <FiltrNuxt />
    </v-col>
  </v-card>
</template>
<script>
import FiltrNuxt from '@/components/FiltrNuxt.vue'
export default {
  components: {
    FiltrNuxt
  },
  data () {
    return {
      items: ['Мех моды', 'Бокс моды', 'Вейпы', 'Жидкости', 'Одноразовые сиграеты'],
      min: 0,
      max: 5000,
      range: [2000, 3000]
    }
  }
}
</script>
<style>
    .poka{
        height: 200vh;
        margin-left: 2vw;
        margin-top: -1vh;
    }
</style>
