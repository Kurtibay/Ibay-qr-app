<template>
    <v-sheet class="d-flex align-center justify-center" style="height: 100vh;">
      <v-card width="500">
        <h2 class="text-center my-6">Signin Page</h2>
        <v-form
          v-model="form"
          @submit.prevent="onSubmit"
        >
          <v-text-field
            v-model="email"
            :readonly="loading"
            :rules="[required]"
            class="mb-2"
            label="Email"
            clearable
            aria-label="Email" type = "Email" prepend-inner-icon="mdi-email-outline"
         ></v-text-field>
  
          <v-text-field
            v-model="password"
            :readonly="loading"
            :rules="[required]"
            label="Password"
            placeholder="Enter your password"
            clearable
            aria-label="Password" type = "Password" prepend-inner-icon="mdi-lock-outline"
          ></v-text-field>
  
          <br>
  
          <v-btn
            :disabled="!form"
            :loading="loading"
            color="success"
            size="large"
            type="submit"
            variant="elevated"
            block
          >
            Sign In
          </v-btn>
        </v-form>
      </v-card>
    </v-sheet>
  </template>
  <script setup>
  import { ref } from 'vue'

  const form = ref(false)
  const email = ref(null)
  const password = ref(null)
  const loading = ref(false)

  function onSubmit () {
    if (!form.value) return
    loading.value = true
    setTimeout(() => (loading.value = false), 2000)
  }
  function required (v) {
    return !!v || 'Field is required'
  }
</script>

<script>
export default {
    layout: "auth"
}
</script>