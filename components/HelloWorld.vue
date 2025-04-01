<template>
  <div class="hello-world-card">
    <h3>{{ greeting }}</h3>
    <p>Dies ist eine Testkomponente aus GitHub!</p>
    <p v-if="userName">Hallo, {{ userName }}!</p>
    <button @click="emitTestEvent">Test Event Senden</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, computed } from 'vue';

// Props Definition (damit WeWeb sie konfigurieren kann)
const props = defineProps({
  userName: {
    type: String,
    required: false,
    default: 'Welt' // Standardwert, falls nichts übergeben wird
  },
  useFormalGreeting: {
    type: Boolean,
    required: false,
    default: false
  }
});

// Emits Definition (damit die Komponente mit WeWeb kommunizieren kann)
const emit = defineEmits(['testEvent']);

// Berechnete Eigenschaft basierend auf Prop
const greeting = computed(() => {
  return props.useFormalGreeting ? 'Guten Tag!' : 'Hallo!';
});

// Methode, um das Event auszulösen
function emitTestEvent() {
  console.log('Button geklickt, sende testEvent...');
  // Sendet das Event 'testEvent' mit dem aktuellen Benutzernamen als Daten
  emit('testEvent', props.userName);
}
</script>

<style scoped>
.hello-world-card {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  margin: 10px;
  background-color: #f9f9f9;
  text-align: center;
}
h3 {
  color: #333;
}
p {
  color: #555;
}
button {
  margin-top: 10px;
  padding: 8px 15px;
  cursor: pointer;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
}
button:hover {
  background-color: #0056b3;
}
</style>