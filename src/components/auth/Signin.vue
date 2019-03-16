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

          <v-btn
            :disabled="!valid"
            color="success"
            @click="validate"
          >
            Login
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
import firebase from 'firebase'
export default {

  data: () => ({

    passwordShow: false,
    valid: true,
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
    ],
    password: '',
    passwordRules: [
      v => !!v || 'Password is Required'
    ]
  }),

  methods: {

    validate () {
      if (this.$refs.form.validate()) {
        this.snackbar = true
        this.loginWithFirebase()
      }
    },

    reset () {
      this.$refs.form.reset()
    },

    loginWithFirebase () {
      firebase.auth().signInWithEmailAndPassword(this.email, this.password)
        .then((response) => {
          alert('success')
          console.log(response)
        })
        .catch((error) => {
          alert('failure')
          debugger
          console.log(error)
        })
    }
  }
}
</script>
