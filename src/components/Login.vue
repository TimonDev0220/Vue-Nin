<template>
  <div class="hello">
    <h1>Login</h1>
    <input id="login_err"/>
    <div class="login_id_div">
      <label class="login_id_label">ID: </label>
      <input class="login_input" />
    </div>
     <div className="Form_footer">
        <img className="toimg" src="../assets/images/register_png1.png" alt="loading"/>
        <img className="hereimg" src="../assets/images/register_png2.png" alt="loading" />
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  background-color: #bbbbbb;
  padding: 10px;
  border:none;
  border-radius: 10px 10px 10px 10px;
  box-shadow: 5px 5px 5px #cccccc;
  width: 500px;
  margin: auto;
  margin-top: 220px;
}
h1 {
  margin-top: 10px;
  font-size: 45px;
}
#login_err {
  font-size:20px;
  background-color: #bbbbbb;
  border:none;
  color: white;
  display: none;
}
.login_id_div {
  margin: auto;
}
.login_id_label {
  font-size: 45px;
  color: white;
}
.login_input {
  width: 350px;
  background-color: black;
  color: white;
  border: none;
  border-radius: 5px 5px 5px 5px;
  font-size: 30px;
  padding: 5px;
  padding-top: 10px;
  padding-left: 15px;
}
</style>
