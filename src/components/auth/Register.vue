<template>
  <v-container>
    <v-layout row wrap>
      <v-flex>
        <v-form
          ref="form"
          v-model="valid"
          lazy-validation
          >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>

          <v-text-field
            v-model="password"
            :rules="passwordRules"
            label="Password"
            required
            :append-icon="passwordShow ? 'visibility' : 'visibility_off'"
            :type="passwordShow ? 'text' : 'password'"
             @click:append="passwordShow = !passwordShow"
          ></v-text-field>

          <v-text-field
            v-model="confirmPassword"
            label="confirm Password"
            :rules="passwordRules"
            required
            :append-icon="confirmPasswordShow ? 'visibility' : 'visibility_off'"
            :type="confirmPasswordShow ? 'text' : 'password'"
             @click:append="confirmPasswordShow = !confirmPasswordShow"
          ></v-text-field>

          <v-btn
            :disabled="!valid"
            color="success"
            @click="validate"
          >
            Register
          </v-btn>

          <v-btn
            color="error"
            @click="reset"
          >
            Reset Form
          </v-btn>
        </v-form>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {

  data: () => ({
    passwordShow: false,
    confirmPasswordShow: false,
    valid: true,
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
    ],
    password: '',
    confirmPassword: '',
    passwordRules: [
      v => !!v || 'Password and Confirm password Required'
    ]
  }),

  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    reset () {
      this.$refs.form.reset()
    }
  }
}
</script>
