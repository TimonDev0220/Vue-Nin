<template>
  <div class="hello">
    <h1>Register</h1>
    <div class="login_id_div">
      <label class="register_id_label">Skype: </label>
      <input :value="msg" @input="onInput" class="register_input" />
    </div>
    <div class="register_linkimg">
      <img class="toimg" src="../assets/images/login_png1.png" alt="loading"/>
      <img class="hereimg" src="../assets/images/register_png2.png" alt="loading" @click="goLogin"/>
    </div>
    <div class="register_btndiv" @click="Register">
    </div>
  </div>
</template>

<script>
import {router} from '../router';
import axios from 'axios'

export default {
  data () {
    return {
      msg: ''
    }
  },
  methods: {
    goLogin() {
    	 return router.push('/');
    },
    Register() {
    	if(this.msg == "") {
    		alert("Field is required!");
    		return;
    	}
    	else {
			axios.post(`http://localhost:8000/api/register`, { user_skypeid: this.msg })
		      .then(res => {
		        alert("Register success!");
		      })
		       .catch(err => {
		        alert("You registered already!");
		       })
			}
    },
    onInput(e) {
    	this.msg = e.target.value
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  background-color: rgb(191, 191, 191);
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
.register_id_div {
  margin: auto;
}
.register_id_label {
  font-size: 40px;
  color: white;
}
.register_input {
  width: 300px;
  background-color: black;
  color: white;
  border: none;
  border-radius: 5px 5px 5px 5px;
  font-size: 30px;
  padding: 5px;
  padding-top: 10px;
  padding-left: 15px;
}
.register_linkimg {
  margin-top: 20px;
}
.toimg {
  width: 350px;
}
.hereimg {
  width: 130px;
  height: 60px;
}
.hereimg:hover {
  width: 135px;
  height: 65px;
}
.register_btndiv {
  background-image: url("http://localhost:8080/static/images/register3.png");
  width: 185px;
  height: 55px;
  margin: auto;
}
.register_btndiv:hover {
  background-image: url("http://localhost:8080/static/images/register4.png");
  margin: auto;
  transition: 900ms;
}
</style>