<template>
  <q-select
    v-model="locale"
    :options="localeOptions"
    dense
    borderless
    emit-value
    map-options
    options-dense
    style="min-width: 100px"
  >
    <template v-slot:prepend>
      <q-icon name="language" />
    </template>
  </q-select>
</template>

<script setup lang="ts">
import { useI18n } from 'vue-i18n';

const { locale } = useI18n();

const localeOptions = [
  { value: 'de-CH', label: 'Deutsch (CH)' }
];
</script>
