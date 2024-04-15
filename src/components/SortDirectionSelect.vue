<template>
  <div class="sort-buttons">
    {{ title }}:
    <v-tooltip text="По возрастанию">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-arrow-up"
          density="compact"
          variant="tonal"
          class="sort-buttons__btn"
          :class="{ active: isActive('asc') }"
          color="blue"
          @click="setSortDirection('asc')"
        />
      </template>
    </v-tooltip>

    <v-tooltip text="По убыванию">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-arrow-down"
          density="compact"
          variant="tonal"
          class="sort-buttons__btn"
          :class="{ active: isActive('desc') }"
          color="blue"
          @click="setSortDirection('desc')"
        />
      </template>
    </v-tooltip>

    <v-tooltip text="Без сортировки">
      <template v-slot:activator="{ props }">
        <v-btn
          v-bind="props"
          icon="mdi-close"
          density="compact"
          variant="tonal"
          class="sort-buttons__btn"
          :class="{ active: isActive('none') }"
          color="blue"
          @click="setSortDirection('none')"
        />
      </template>
    </v-tooltip>
  </div>
</template>

<script setup>
const props = defineProps({
  modelValue: {
    type: String,
    required: true,
  },

  title: {
    type: String,
    required: true,
  },
});

function isActive(direction) {
  return direction === props.modelValue;
}

const emits = defineEmits({
  "update:modelValue": (value) => ["none", "asc", "desc"].includes(value),
});

function setSortDirection(direction) {
  emits("update:modelValue", direction);
}
</script>

<style lang="scss" scoped>
.sort-buttons {
  color: azure;
  display: flex;
  flex-direction: row;
  gap: 10px;

  &__btn {
    background-color: azure;
  }
}
</style>
