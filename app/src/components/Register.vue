<template>
    <div class="registration-form">
      <h2>New member Registration Form</h2>
      <form @submit.prevent="submitForm">
        <label for="name">Full Name:</label>
        <input type="text" id="name" v-model="formData.name" required>
        
        <label for="email">Email Address:</label>
        <input type="email" id="email" v-model="formData.email" required>
        
        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" v-model="formData.phone" required>
        
        <label for="entry_category">Entry Category:</label>
        <select id="entry_category" v-model="formData.entryCategory">
          <option value="Individual">Individual</option>
          <option value="Minor">Minor</option>
          <option value="Organization">Organization</option>
        </select>
        
        <input type="submit" value="Register">
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        formData: {
          name: '',
          email: '',
          phone: '',
          entryCategory: 'Individual'
        }
      };
    },
    methods: {
      submitForm() {
        // Here you can handle form submission, e.g., send data to server or perform validation
        console.log('Form submitted with data:', this.formData);
        // Reset form after submission if needed
        this.formData = {
          name: '',
          email: '',
          phone: '',
          entryCategory: 'Individual'
        };
      }
    }
  };
  </script>
  
  <style scoped>
  .registration-form {
    width: 400px;
    margin: 40px auto;
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .registration-form label {
    display: block;
    margin-bottom: 10px;
  }
  
  .registration-form input[type="text"],
  .registration-form input[type="email"],
  .registration-form input[type="tel"],
  .registration-form select {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border: 1px solid #ccc;
  }
  
  .registration-form input[type="submit"] {
    background-color: #4CAF50;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .registration-form input[type="submit"]:hover {
    background-color: #3e8e41;
  }
  </style>
  