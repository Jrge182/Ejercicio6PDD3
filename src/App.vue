<template>
  <div>
    <h2>Formulario de contacto</h2>
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="name" placeholder="Nombre" required>
      <input type="email" v-model="email" placeholder="Email" required>
      <input type="text" v-model="subject" placeholder="Asunto">
      <textarea v-model="message" placeholder="Mensaje"></textarea>
      <button type="submit">Enviar</button>
    </form>

    <div v-if="errors.length">
      <ul>
        <li v-for="error in errors">{{ error }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      subject: "",
      message: "",
      errors: []
    };
  },

  methods: {
    onSubmit() {
      // Validar formulario
      this.errors = [];

      if (!this.name) {
        this.errors.push("El nombre es obligatorio.");
      }

      if (!this.email.match(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/)) {
        this.errors.push("El email no es válido.");
      }

      if (!this.subject) {
        this.errors.push("El asunto es obligatorio.");
      }

      if (!this.message) {
        this.errors.push("El mensaje es obligatorio.");
      }

      // Si no hay errores, enviar el formulario
      if (!this.errors.length) {
        // Enviar el formulario al servidor
        // ...
      }
    }
  }
};
</script>
