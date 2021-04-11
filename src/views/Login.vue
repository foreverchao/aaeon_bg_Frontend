<template>
 <div class="center">
    <img src="../assets/icon/logo.png" >
    <h1 style="font-family:OCR A Std, monospace;">Admin Login</h1>
    <div class="login-form">
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field v-model="email" :rules="emailRules" label="E-mail" placeholder="請輸入Email" required></v-text-field>

        <v-text-field type="password" v-model="password" :rules="passwordRules" label="Password" placeholder="請輸入密碼" required></v-text-field>
        <v-btn color="primary" elevation="2" class="mr-4" @click="Login">
            Login
        </v-btn>
      </v-form>
    </div>
  </div>
</template>

<script>
const userInfo = {
  emailAddr: "1111@test.com.tw" ,
  passWord: "1"
}
export default {
  name: "Login",
  components: {},
  data: () => ({
    valid: true,
    password: "",
    passwordRules: [(v) => !!v || "PassWord is required"],
    email: "",
    emailRules: [(v) => !!v || "E-mail is required", (v) => /.+@.+\..+/.test(v) || "E-mail must be valid"],
    select: null,
  }),
  methods: {
    validate() { //將校驗所有輸入並返回它們是否都有效
      this.$refs.form.validate();
    },
    reset() { //將清除所有輸入並重置校驗錯誤
      this.$refs.form.reset();
    },
    resetValidation() { //只是重置輸入校驗，而不會更改其狀態
      this.$refs.form.resetValidation();
    },
    Login() {
      if (this.password == userInfo.passWord && this.email == userInfo.emailAddr){
          this.$router.push("/Home");
      }
      else if (this.password == "" || this.email == ""){
        this.$refs.form.validate();
      } 
      else {
        alert("信箱或密碼錯誤");
        this.$refs.form.reset();
      }
    },
  },
};
</script>

<style scoped>
.login-form {
  margin: auto;
  position: relative;
  width: 30%;
  padding: 10px;
  border: 3px solid darkgray;
}
.center {
  vertical-align: middle;
  padding:125px 0px;
  text-align: center;
  margin-block-start: 0px;
}
</style>