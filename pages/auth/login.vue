<template>
  <v-form ref="form" v-model="valid" method="POST">
    <v-text-field v-model="email" name="email" :counter="10" :rules="emailRules" label="Email" required></v-text-field>

    <v-text-field v-model="password" name="password" :rules="passwordRules" label="Password" required></v-text-field>

    <v-btn color="default" class="mt-5" :disabled="!valid" @click="submit">Login</v-btn>
  </v-form>
</template>

<script>
export default {
  data: () => ({
    valid: false,

    email: '',
    password: '',

    emailRules: [
      (v) => !!v || 'Email is required',
      (v) => (v && v.length <= 20) || 'Email must be less than 20 characters'
    ],
    passwordRules: [
      (v) => !!v || 'Password is required',
      (v) => (v && v.length >= 6) || 'Password must more than 6 characters'
    ]
  }),

  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        this.$refs.form.$el.submit();
      }
    }
  }
};
</script>
