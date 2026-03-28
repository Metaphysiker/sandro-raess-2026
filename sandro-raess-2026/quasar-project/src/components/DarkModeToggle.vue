<template>
  <q-btn
    flat
    dense
    round
    :icon="$q.dark.isActive ? 'light_mode' : 'dark_mode'"
    @click="toggleDarkMode"
  >
    <q-tooltip>{{ $q.dark.isActive ? 'Light Mode' : 'Dark Mode' }}</q-tooltip>
  </q-btn>
</template>

<script setup lang="ts">
import { useQuasar } from 'quasar';
import { onMounted } from 'vue';

const $q = useQuasar();

// Load saved preference on mount
onMounted(() => {
  const savedDarkMode = localStorage.getItem('darkMode');
  if (savedDarkMode !== null) {
    $q.dark.set(savedDarkMode === 'true');
  }
});

function toggleDarkMode() {
  $q.dark.toggle();
  // Save preference
  localStorage.setItem('darkMode', String($q.dark.isActive));
}
</script>
