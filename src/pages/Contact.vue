<template>
  <div v-if="isLoading" >
    <div class="center">
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
      <div class="wave"></div>
    </div>
  </div>
    <div v-else class="container">
      <div class="row-contact">
        <div class="contact-img">
          <img src="@/assets/img/contact.svg" alt="contact" />
        </div>
        <div class="form-contact">
          <h2>Contact</h2>
          <div class="input-form">
            <label for="">Name</label>
            <input type="text" v-model="form.name" class="input" placeholder="Enter Name" />
          </div>
          <div class="input-form">
            <label for="">email</label>
            <input type="text" v-model="form.email" class="input" placeholder="Enter Name" />
          </div>
          <div class="input-form">
            <label for="">Phone</label>
            <input type="text" v-model="form.phone" class="input" placeholder="Enter Name" />
          </div>
          <div class="input-form">
            <label for="">Message</label>
            <textarea v-model="form.message" name="" id="" cols="20" placeholder="Enter Message"></textarea>
          </div>
          <div class="input-form">
            <div>
              <button @click="submit" class="btn-service">Submit</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script >
  import { Post } from '@/Api/index.js';
  export default {
    data() {
      return {
        form: {
          name: '',
          email: '',
          phone: '',
          message: '',
        },
        isLoading: false,
      };
    },
  
    methods: {
      async submit() {
        this.isLoading = true;
        const response = await Post('contact', this.form);
        if (response.status == 200) {
          this.form = {
            name: '',
            email: '',
            phone: '',
            message: '',
          };
          alert('data berhasil ditambahkan');
        }
        this.isLoading = false;
      },
    },
  };
  </script>
  <style scoped>
  .row-contact {
    display: flex;
    margin-top: 10px;
    align-items: center;
  }
  .contact-img {
    width: 50%;
  }
  .form-contact {
    width: 50%;
    display: flex;
    flex-direction: column;
  }
  .contact-img img {
    width: 80%;
  }
  .input-form {
    width: 80%;
    position: relative;
    display: flex;
    margin: 8px 5px;
    flex-direction: column;
  }
  .input-form label {
    margin-bottom: 5px;
  }
  .input {
    width: 100%;
    padding: 12px 15px;
    height: 20px;
    font-size: 16px;
    border: 1px solid #dddddd;
    border-radius: 5px;
    color: black;
    box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.05);
    /* border: none; */
  }
  .input:focus {
    outline: none;
  }

  .center {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #000;
  }
  .wave {
    width: 5px;
    height: 100px;
    background: linear-gradient(45deg, cyan, #fff);
    margin: 10px;
    animation: wave 1s linear infinite;
    border-radius: 20px;
  }
  .wave:nth-child(2) {
    animation-delay: 0.1s;
  }

  .wave:nth-child(3) {
  animation-delay: 0.2s;
  }
  .wave:nth-child(4) {
    animation-delay: 0.3s;
  }
  .wave:nth-child(5) {
    animation-delay: 0.4s;
  }
  .wave:nth-child(6) {
    animation-delay: 0.5s;
  }
  .wave:nth-child(7) {
    animation-delay: 0.6s;
  }
  .wave:nth-child(8) {
  animation-delay: 0.7s;
  }
  .wave:nth-child(9) {
    animation-delay: 0.8s;
  }
  .wave:nth-child(10) {
    animation-delay: 0.9s;
  }

  @keyframes wave {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1);
    }
    100% {
      transform: scale(0);
    }
  }
  
  </style>
  