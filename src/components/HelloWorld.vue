<script setup>
  import { ref, reactive } from 'vue';
  const counter = ref(0);
  const person = ref({
    firstName: '',
    lastName: '',
    changeIfStartsWith: function (needle, field, newValue) {
      if (this[field].startsWith(needle)) {
        this[field] = newValue;
      }
    }
  });
  const handleChangeFirstName = (needle, field, newValue) => {
    if (person.value[field].startsWith(needle)) {
      person.value[field] = newValue 
    }
  };
  person.value.firstName = 'Misael';
  const myToken = ref(null);
  const handleSetId = () => {
    myToken.value = 'id';
  };

  const handleSetName = () => {
    myToken.value = 'name';
  };
</script>
<template>
  <div class="w-8/12 mx-auto my-4">
    <input 
      :value="counter"
      :[myToken]="'name'"
      type="text"
      placeholder="Name"/>
    <button 
      class="rounded px-3 py-2 text-center text-white bg-green-600 mt-3"
      @click="handleSetId"
      >
      Set id
    </button>
    <button 
      class="rounded px-3 py-2 text-center text-white bg-blue-600 mt-3"
      @click="handleSetName">
      Set name
    </button>
    <div>
      <p>{{ person.firstName }}</p>
      <input 
        type="text" 
        v-model="person.firstName"
        class="border-2">
        <button 
          class="rounded px-3 py-2 text-center text-white bg-green-600 mt-3"
          @click="() => handleChangeFirstName('mis', 'firstName', 'Juan')">Change</button>
    </div>
  </div>
</template>