<template>
  <v-form v-model="valid" @:submit.prevent="onSubmit">
    <v-container>
      <v-row>
        <v-col cols="4">
          <v-text-field
            v-model="lastname"
            :rules="nameRules"
            label="Last name"
            required
          ></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4">
          <v-text-field
            v-model="email"
            label="E-mail"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-btn type="submit">submit</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      lastname: 'test',
      email: 'test@ttest.com',
      valid: false,
      nameRules: [
        (v) => !!v || 'Name is required',
        (v) => v.length <= 10 || 'Name must be less than 10 characters'
      ],
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+/.test(v) || 'E-mail must be valid'
      ]
    }
  },
  methods: {
    onSubmit(values) {
      console.log('values', values, this)
    }
  }
}
</script>
