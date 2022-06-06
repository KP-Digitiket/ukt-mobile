<template>
  <v-container>
    <v-toolbar>
      <h1 class="heading">Daftar</h1>
    </v-toolbar>
    <p class="sub-heading">Masukkan data untuk buat akun baru</p>
    <v-img src="../../public/img/daftar.png" class="img-heading"></v-img>
    <p></p>
    <v-form ref="form" v-model="valid" lazy-validation>
      <label for="">Nama Lengkap</label>
      <v-text-field
        v-model="name"
        :rules="nameRules"
        label="Masukan nama Lengkap"
        required
        outlined
        color="success"
      ></v-text-field>
      <label for="">Masukan Handphone</label>
      <v-text-field
        v-model="phone"
        label="Masukan Handphone"
        outlined
      ></v-text-field>
      <label for="">Masukan Email</label>
      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="Masukan Email"
        required
        outlined
      ></v-text-field>
      <label for="">Masukan Password</label>
      <v-text-field
        v-model="password"
        :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
        :rules="passwordRules"
        label="Masukan Password"
        required
        :type="showPassword ? 'text' : 'password'"
        outlined
        @click:append="showPassword = !showPassword"
      ></v-text-field>

      <v-btn
        :disabled="!valid"
        color="btn-primary white--text"
        class="mr-4"
        block
        @click="validate"
      >
        Daftar
      </v-btn>
    </v-form>
    <p class="mt-5">
      Sudah memiliki akun?
      <a href="/login">Masuk</a>
    </p>
  </v-container>
</template>
<script>
export default {
  name: 'daftar',
  data: () => ({
    valid: true,
    name: '',
    nameRules: [
      (v) => !!v || 'Name is required',
      (v) => (v && v.length <= 10) || 'Name must be less than 10 characters',
    ],
    phone: '',
    email: '',
    emailRules: [
      (v) => !!v || 'E-mail is required',
      (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    showPassword: false,
    password: '',
    passwordRules: [
      (v) => !!v || 'Password is required',
      (v) => (v && v.length >= 6) || 'Min 6 Characters',
    ],
  }),

  methods: {
    validate() {
      this.$refs.form.validate()
    },
    reset() {
      this.$refs.form.reset()
    },
    resetValidation() {
      this.$refs.form.resetValidation()
    },
  },
}
</script>

<style scoped>
.v-sheet.v-toolbar:not(.v-sheet--outlined) {
  box-shadow: none;
}
.heading {
  font-weight: 600;
  font-size: 18px;
  color: #185a46;
  text-align: center;
  margin: 0 auto;
}
.v-image.v-responsive {
  position: relative;
  overflow: hidden;
  flex: 1 0 auto;
  margin-top: -20%;
  display: flex;
}
.sub-heading {
  margin: 0 auto;
  font-size: 12px;
  text-align: center;
  color: #a4d693;
}
label {
  margin-bottom: 8%;
  line-height: 18px;
  color: #185a46;
  font-weight: 600;
  font-size: 12px;
}

p {
  text-align: center;
  color: #d9d2c7;
  font-size: 10px;
  font-weight: 500;
}

p a {
  color: #38af79;
  font-size: 10px;
  font-weight: 500;
  text-decoration: none;
}
/* .v-text-field--outlined > .v-input__control > .v-input__slot {
  background: transparent;
} */
</style>
