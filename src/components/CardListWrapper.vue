<template>
  <div class="card-list-wrapper">
    <SortDirectionSelect v-model="sortRatingDirection" title="Рейтинг" />

    <CardList :options="options" :sortRatingDirection="sortRatingDirection" />
  </div>
</template>

<script setup>
import CardList from "./CardList.vue";
import SortDirectionSelect from "./SortDirectionSelect.vue";
import { ref } from "vue";

const props = defineProps({
  options: {
    type: Object,
    required: true,
  },
});

const sortRatingDirection = ref("none");
</script>

<style lang="scss" scoped>
.card-list-wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>
