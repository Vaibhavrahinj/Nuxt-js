<template>
<div class="flex justify-center">
  <h1>Contact Us!</h1>
    <form @submit.prevent="handleSubmit">
    <input v-model="form.name" type="text" name="name" placeholder="Enter name" required/>
    <input v-model="form.email" type="email" name="email" placeholder="Enter email" required/>
    <textarea v-model="form.message" placeholder="Enter message" name="message" required></textarea>
    <button type="submit">Send</button>
  </form>
  </div>
</template>

<script>

  // import axios from 'axios';

  export default {
    name: 'ContactForm',
    data() {
      return {
        form: {
          name: "",
          email: "",
          message: "",
        },
      };
    },
    methods: {
      handleSubmit: async function() {
        const formData = new FormData();

        for (let [key, value] of Object.entries(this.form)) {
          formData.append(key, value);
        }

        await axios
          .post("{Formeezy-Endpoint}", formData)
          .then(({ data }) => {
            const { redirect } = data;
            // Redirect used for reCAPTCHA and/or thank you page
            window.location.href = redirect;
          })
          .catch((e) => {
            window.location.href = e.response.data.redirect;
          });
      }
    }
  };
</script>
