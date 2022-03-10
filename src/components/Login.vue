<template>
  <div class="hello">
    <h1>Login</h1>
    <input :value="err" id="login_err"/>
    <div class="login_id_div">
      <label class="login_id_label">ID: </label>
      <input :value="msg" @input="onInput" class="login_input" />
    </div>
    <div class="login_linkimg">
      <img class="toimg" src="../assets/images/register_png1.png" alt="loading"/>
      <img class="hereimg" src="../assets/images/register_png2.png" alt="loading" @click="goRegister"/>
    </div>
    <div class="login_btndiv" @click="Login">
    </div>
  </div>
</template>

<script>
import {router} from '../router';
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '',
      err: '',
    }
  },
  methods: {
    goRegister() {
      return router.push('/register');
    },
    onInput(e) {
      this.msg = e.target.value
    },
    Login() {
    if(this.msg == "") {
      alert("filed is required");
      return;
    }
      axios.post('http://localhost:8000/api/login', { user_id: this.msg})
      .then(res=> {
          if(res.data.id === "admin") {
            
          }
          else {
            localStorage.setItem('currentUser', res.data.id);
            this.goOn(res.data.id);
          }
        })
      .catch(err => {
        let str1 = String(err);
        str1 = str1.slice(-1);
        var errorcode = "";
        var errinput = document.getElementById("login_err")
        errinput.setAttribute("style", "display: block; margin: auto;")
        switch(str1) {
          case '0':
            errorcode = "The field is required";
            this.err = errorcode;
            setTimeout(this.myFunction, 3000);
            break;
          case '1':
            errorcode = "Wait our Permission";
            this.err = errorcode;
            setTimeout(this.myFunction, 3000);
            break;
          case '4':
            errorcode = "Your account does not exist";
            this.err = errorcode;
            setTimeout(this.myFunction, 3000);
            break;
          default:
            break;
        }
      })
    },
    myFunction() {
      var errinput = document.getElementById("login_err")
      errinput.setAttribute("style", "display: none;")
    },
    goOn(flag) {
      axios.get('http://localhost:8000/api/get/avatar' + '/' + flag)
          .then(result => {
            localStorage.setItem('currentUser_avatar', result.data.Leader_avatar);
            return router.push('/Main')
            localStorage.setItem('currentUser_avatar', result.data.Leader_avatar);
          })
          .catch(err=>console.log(err));
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
#login_err {
  font-size:20px;
  background-color: #bbbbbb;
  border:none;
  color: white;
  display: none;
  width: 240px;
  margin-bottom: 10px;
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
.login_linkimg {
  margin-top: 20px;
}
.toimg {
  width: 350px;
}
.hereimg {
  width: 120px;
  height: 55px;
}
.hereimg:hover {
  width: 125px;
  height: 60px;
}
.login_btndiv {
  background-image: url("http://localhost:8080/static/images/comein.png");
  width: 185px;
  height: 55px;
  margin: auto;
}
.login_btndiv:hover {
  background-image: url("http://localhost:8080/static/images/login2.png");
  margin: auto;
  transition: 900ms;
  transform: rotate(360deg);
}
</style>