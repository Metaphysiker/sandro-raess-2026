<template>
  <q-card class="chat-component" flat bordered>
    <q-card-section class="chat-header bg-primary text-white">
      <div class="text-h6">Chat</div>
    </q-card-section>

    <q-separator />

    <q-card-section class="chat-messages-container">
      <q-chat-message
        v-for="msg in messages"
        :key="msg.id"
        :name="msg.name"
        :text="[msg.text]"
        :sent="msg.sent"
        :stamp="msg.stamp"
        :bg-color="msg.sent ? 'primary' : 'grey-4'"
      />
    </q-card-section>

    <q-separator />

    <q-card-section class="chat-input">
      <div class="row q-gutter-sm">
        <q-input
          v-model="newMessage"
          outlined
          dense
          placeholder="Type a message..."
          class="col"
          @keyup.enter="sendMessage"
          color="primary"
          bg-color="transparent"
        >
          <template v-slot:append>
            <q-btn
              round
              dense
              flat
              icon="send"
              color="primary"
              @click="sendMessage"
              :disable="!newMessage.trim()"
            />
          </template>
        </q-input>
      </div>
    </q-card-section>
  </q-card>
</template>

<script setup lang="ts">
import { ref } from "vue";

interface ChatMessage {
  id: number;
  name: string;
  text: string;
  sent: boolean;
  stamp: string;
}

const messages = ref<ChatMessage[]>([
  {
    id: 1,
    name: "Assistant",
    text: "Hello! How can I help you today?",
    sent: false,
    stamp: "10:00 AM",
  },
  {
    id: 2,
    name: "You",
    text: "Hi! Just testing the chat.",
    sent: true,
    stamp: "10:01 AM",
  },
]);

const newMessage = ref("");

const sendMessage = () => {
  if (!newMessage.value.trim()) return;

  const now = new Date();
  const stamp = now.toLocaleTimeString("en-US", {
    hour: "numeric",
    minute: "2-digit",
  });

  messages.value.push({
    id: messages.value.length + 1,
    name: "You",
    text: newMessage.value,
    sent: true,
    stamp,
  });

  newMessage.value = "";
};
</script>

<style scoped lang="scss">
.chat-component {
  width: 100%;
  height: calc(100vh - 150px);
  display: flex;
  flex-direction: column;
}

.chat-messages-container {
  flex: 1;
  overflow-y: auto;
}

.chat-header {
  padding: 12px 16px;
  flex-shrink: 0;
}

.chat-input {
  padding: 12px 16px;
  flex-shrink: 0;
}

.chat-input :deep(.q-field__native) {
  color: currentColor !important;
}
</style>
