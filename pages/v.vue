<template>
    <div>
      <!-- Step indicators -->
      <div class="w-100 pa-1 d-flex ga-3 step-indicators">
        <div :class="['step', { active: step === 1, completed: step > 1 }]"><span>Step 1</span></div>
        <div :class="['step', { active: step === 2, completed: step > 2 }]"><span>Step 2</span></div>
        <div :class="['step', { active: step === 3, completed: step > 3 }]"><span>Step 3</span></div>
      </div>
  
      <!-- Form for Step 1 -->
      <div v-if="step === 1">
        <form @submit.prevent="nextStep">
          <div>
            <label for="name">Name:</label>
            <input type="text" id="name" v-model="formData.name" />
            <span v-if="errors.name">{{ errors.name }}</span>
          </div>
        </form>
      </div>
  
      <!-- Form for Step 2 -->
      <div v-if="step === 2">
        <form @submit.prevent="nextStep">
          <div>
            <label for="email">Email:</label>
            <input type="email" id="email" v-model="formData.email" />
            <span v-if="errors.email">{{ errors.email }}</span>
          </div>
        </form>
      </div>
  
      <!-- Form for Step 3 -->
      <div v-if="step === 3">
        <form @submit.prevent="nextStep">
          <div>
            <label for="phone">Phone:</label>
            <input type="text" id="phone" v-model="formData.phone" />
            <span v-if="errors.phone">{{ errors.phone }}</span>
          </div>
        </form>
      </div>
  
      <!-- Navigation Buttons -->
      <div class="navigation-buttons">
        <button @click="prevStep" v-if="step > 1">Preview</button>
        <button @click="nextStep">{{ step === 3 ? 'Submit' : 'Next' }}</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const step = ref(1); // Current step
  const formData = ref({
    name: '',
    email: '',
    phone: '',
  });
  const errors = ref({});
  
  // Validation function
  const validateStep = () => {
    errors.value = {};
    if (step.value === 1 && !formData.value.name) {
      errors.value.name = 'Name is required';
    } else if (step.value === 2 && !formData.value.email) {
      errors.value.email = 'Email is required';
    } else if (step.value === 3 && !formData.value.phone) {
      errors.value.phone = 'Phone is required';
    }
  
    return Object.keys(errors.value).length === 0;
  };
  
  // Move to the next step
  const nextStep = () => {
    if (validateStep()) {
      if (step.value < 3) {
        step.value++;
      } else {
        // Submit form
        console.log('Form Data:', formData.value);
        alert('Form submitted successfully!');
      }
    }
  };
  
  // Move to the previous step
  const prevStep = () => {
    if (step.value > 1) {
      step.value--;
    }
  };
  </script>
  
  <style scoped>
  /* Styles for step indicators and buttons */
  .step-indicators {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  
  .step {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: lightgray; /* Default inactive state */
    font-weight: bold;
  }
  
  .active {
    background-color: green;
    color: white;
  }
  
  .completed {
    background-color: blue;
    color: white;
  }
  
  .navigation-buttons {
    margin-top: 20px;
  }
  
  button {
    margin-right: 10px;
    padding: 10px 20px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  button:disabled {
    background-color: lightgray;
    cursor: not-allowed;
  }
  
  span {
    color: red;
    font-size: 12px;
  }
  </style>
  