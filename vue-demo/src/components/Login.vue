<template>
  <div class="Login">
    <h1>{{ msg }}</h1>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="用户名">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="form.password"></el-input>
      </el-form-item>
      <el-button type="primary" @click="login">登录</el-button>
      <el-button type="info">重置</el-button>
    </el-form>
    <button @click="demoClick">tes434444444t</button>
    <Home :msgJson="msgJson" :author="myName"></Home>
  </div>
</template>
<script>
import Home from "../components/Home";
export default {
  name: "Login",

  data: function() {
    return {
      msg: "test  24234234",
      msgJson: { msg: "头部传参", msgFlog: true },
      myName: "lyy",
      form: {
        name: "",
        password: ""
      }
    };
  },
  methods: {
    demoClick: function() {
      this.$router.push({ path: "/Home" });
    },
    login: function() {
      console.log(this.form);
      this.$axios
        .get("user/get")
        .then(res => {
          console.log(res);
          this.$router.push({
            name: "Home",
            // params: {
            //   name: "name",
            //   dataObj: this.msgJson
            // },
            props: { msgJson: this.msgJson }
          });
        })
        .catch(err => console.log(err));
    }
  },
  components: {
    Home: Home
  }
};
</script>
