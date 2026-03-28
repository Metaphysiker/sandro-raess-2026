<template>
  <q-footer elevated>
    <q-toolbar>
      <q-toolbar-title>
        <div class="text-center">{{ t("appTitle") }}</div>
      </q-toolbar-title>
    </q-toolbar>
  </q-footer>
</template>

<script setup lang="ts">
import { useI18n } from "vue-i18n";

const { t } = useI18n();
</script>
