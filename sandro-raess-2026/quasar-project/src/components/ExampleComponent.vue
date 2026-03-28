<template>
  <div>
    <p>{{ title }}</p>

    <chat-component />
    <p>Translated Text: {{ $t("failed") }}</p>
    <ul>
      <li v-for="todo in todos" :key="todo.id" @click="increment">
        {{ todo.id }} - {{ todo.content }}
      </li>
    </ul>
    <p>Count: {{ todoCount }} / {{ meta.totalCount }}</p>
    <p>Active: {{ active ? "yes" : "no" }}</p>
    <p>Clicks on todos: {{ clickCount }}</p>

    <div class="q-mt-md">
      <p>Selected Color: {{ color }}</p>
      <q-color v-model="color" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";
import type { Todo, Meta } from "./models";
import ChatComponent from "./ChatComponent.vue";

interface Props {
  title: string;
  todos?: Todo[];
  meta: Meta;
  active: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  todos: () => [],
});

const clickCount = ref(0);
const color = ref("#1976D2");

function increment() {
  clickCount.value += 1;
  return clickCount.value;
}

const todoCount = computed(() => props.todos.length);
</script>
