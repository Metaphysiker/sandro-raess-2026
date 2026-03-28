<template>
  <div class="q-pa-md">
    <div class="text-h4 text-center q-mb-lg">Get In Touch</div>
    <div class="text-subtitle1 text-center text-grey-7 q-mb-xl">
      Have a project in mind? Let's work together!
    </div>

    <div class="row justify-center">
      <div class="col-12 col-md-8 col-lg-6">
        <q-card flat bordered>
          <q-card-section>
            <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
              <q-input
                v-model="email"
                type="email"
                label="Email *"
                hint="Your email address"
                lazy-rules
                :rules="[
                  (val) => (val && val.length > 0) || 'Please enter your email',
                  (val) => isValidEmail(val) || 'Please enter a valid email',
                ]"
                outlined
              >
                <template v-slot:prepend>
                  <q-icon name="mail" />
                </template>
              </q-input>

              <q-input
                v-model="phone"
                type="tel"
                label="Phone"
                hint="Your phone number (optional)"
                outlined
              >
                <template v-slot:prepend>
                  <q-icon name="phone" />
                </template>
              </q-input>

              <q-input
                v-model="request"
                type="textarea"
                label="Request *"
                hint="Tell me about your project"
                lazy-rules
                :rules="[
                  (val) => (val && val.length > 0) || 'Please describe your request',
                  (val) =>
                    (val && val.length >= 10) || 'Please provide at least 10 characters',
                ]"
                outlined
                rows="5"
              >
                <template v-slot:prepend>
                  <q-icon name="message" />
                </template>
              </q-input>

              <div class="row justify-end q-gutter-sm">
                <q-btn label="Reset" type="reset" color="grey-7" flat class="q-ml-sm" />
                <q-btn
                  label="Submit"
                  type="submit"
                  color="primary"
                  :loading="submitting"
                />
              </div>
            </q-form>
          </q-card-section>
        </q-card>

        <q-banner v-if="successMessage" class="bg-positive text-white q-mt-md">
          <template v-slot:avatar>
            <q-icon name="check_circle" color="white" />
          </template>
          {{ successMessage }}
        </q-banner>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useQuasar } from "quasar";

const $q = useQuasar();

const emit = defineEmits<{
  (e: 'contact-sent'): void;
}>();

const email = ref("");
const phone = ref("");
const request = ref("");
const submitting = ref(false);
const successMessage = ref("");

const isValidEmail = (val: string): boolean => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailPattern.test(val);
};

const onSubmit = async () => {
  submitting.value = true;
  successMessage.value = "";

  // Simulate API call
  await new Promise((resolve) => setTimeout(resolve, 1000));

  // Show success notification
  $q.notify({
    color: "positive",
    textColor: "white",
    icon: "check_circle",
    message: "Your message has been sent successfully!",
  });

  successMessage.value = "Thank you for reaching out! I will get back to you soon.";
  submitting.value = false;

  // Emit event for parent components
  emit('contact-sent');

  // Reset form after success
  setTimeout(() => {
    onReset();
    successMessage.value = "";
  }, 3000);
};

const onReset = () => {
  email.value = "";
  phone.value = "";
  request.value = "";
};
</script>

<style scoped lang="scss">
.q-card {
  transition: box-shadow 0.3s ease;

  &:hover {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  }
}
</style>
