<template>
    <label class="radio-btn">
      <input 
        type="radio" 
        :name="name" 
        :value="value" 
        v-model="localChecked" 
        @change="handleChange" 
      />
      <div class="btn-label d-flex ga-2">
        {{ label }}
      </div>
    </label>
  </template>
  
  <script>
  import { ref, defineProps, watch, defineEmits } from 'vue';
  
  export default {
    name: 'CheckboxButton',
    props: {
      label: {
        type: String,
        required: true,
      },
      modelValue: {
        type: String,
        default: '',
      },
      value: {
        type: String,
        required: true,
      },
      name: {
        type: String,
        required: true,
      },
    },
    setup(props, { emit }) {
      const localChecked = ref(props.modelValue);
  
      watch(localChecked, (newValue) => {
        emit('update:modelValue', newValue); // Emit the updated value to the parent
      });
  
      const handleChange = () => {
        emit('update:modelValue', props.value); // Emit the selected value
      };
  
      // Watch for changes in props to sync local state with parent
      watch(() => props.modelValue, (newValue) => {
        localChecked.value = newValue;
      });
  
      return {
        localChecked,
        handleChange,
      };
    },
  };
  </script>
  
  <style scoped>
  .radio-btn input[type="radio"] {
    display: none; /* Hide the default radio button */
  }
  
  .radio-btn {
    display: inline-block;
    cursor: pointer; /* Style to show it's clickable */
  }
  
  .radio-btn .btn-label {
    display: flex;
    justify-content: center;
    align-items: center; /* Align icon and text */
    background-color: #eeecec;
    padding: 10px 20px;
    color: white;
    border-radius: 8px;
    font-size: 14px;
    transition: background-color 0.3s;
    color: black;
    width: 100%;
  }
  
  .radio-btn .btn-label i {
    margin-right: 8px; /* Space between icon and text */
    opacity: 0; /* Hide icon initially */
    transition: opacity 0.3s; /* Transition for smooth effect */
  }
  
  .radio-btn input[type="radio"]:checked + .btn-label {
    background-color: #4caf50; /* Change background when checked */
    color: #eeecec;
  }
  
  .radio-btn input[type="radio"]:checked + .btn-label i {
    opacity: 1; /* Show the icon when checked */
  }
  
  .radio-btn .btn-label:hover {
    background-color: #888; /* Add hover effect */
  }
  </style>
  