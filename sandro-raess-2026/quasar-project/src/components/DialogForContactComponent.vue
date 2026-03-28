<template>
  <q-dialog v-model="dialogModel" persistent>
    <q-card style="min-width: 600px; max-width: 1200px; width: 90vw">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6">Kontakt</div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup />
      </q-card-section>

      <q-card-section>
        <ContactComponent @contact-sent="onContactSent" />
      </q-card-section>
    </q-card>
  </q-dialog>
</template>

<script setup lang="ts">
import { computed } from "vue";
import ContactComponent from "./ContactComponent.vue";

interface Props {
  modelValue: boolean;
}

const props = defineProps<Props>();

const emit = defineEmits<{
  (e: "update:modelValue", value: boolean): void;
}>();

const dialogModel = computed({
  get: () => props.modelValue,
  set: (value) => emit("update:modelValue", value),
});

const onContactSent = () => {
  // Auto-close dialog after successful contact form submission
  setTimeout(() => {
    dialogModel.value = false;
  }, 3500);
};
</script>
