<template>
  <div>
    <div class="main_header">
      <div class="main_container1">
        <div class="logo_div">
          <img class="logo_img" src="../assets/images/PNG.png" alt="none" />
        </div>
        <div class="main_title">
          <div class="main_title_img">
          </div>
          <div class="main_tab">
            <button class="tab_btn btn1">TicketList</button>
            <button class="tab_btn btn2">LeaderBoard</button>
            <button class="tab_btn btn3">NinjaShop</button>
          </div>
        </div>
        <div class="main_avatar">
          <div class="avatar_div">
            <img class="avatar_img" :src="currentAva" alt="none" />
          </div>
          <div class="cu_username">
            <input class="cu_user_in" :value="currentName" disabled/>
          </div>
          <div class="logout_div">
            <button class="logout_btn" @click="logout">Logout</button>
          </div>
        </div>
      </div>
    </div>
    <div class="component">
      <ticket />
    </div>
  </div>
</template>

<script>
import {router} from '../router';
import axios from 'axios'
import ticket from './childs/ticket'

export default {
  name: 'Main',
  data () {
    return {
      currentComp: 'ticket',
      currentAva: localStorage.getItem('currentUser_avatar'),
      currentName: localStorage.getItem('currentUser'),
      msg: '',
      err: '',
    }
  },
  components: {
    ticket
  },
  methods: {
   
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main_container1 {
  width: 80%;
  margin: auto;
  display: flex;
  flex-direction: row;
}
.main_header {
  height:120px;
  background: linear-gradient(to right,white, black);
  display: flex;
  flex-direction: row;
}
.logo_div {
  width: 120px;
  display: inline-block;
}
.logo_img {
  width: 120px;
}
.main_title {
  width:70%;
  height: 120px;
  margin-left: 5%;
  display: inline-block;
}
.main_title_img {
  width: 100%;
  height: 60%;
  background-image: url("http://localhost:8080/static/images/header4.png");
  background-size:     cover;     
  background-repeat:   no-repeat;
  background-position: center center; 
}
.main_tab {
  margin-top: 10px;
}
.tab_btn {
  font-size: 17px;
  color: white;
  border: none;
  padding: 9px;
  border-radius: 3px;
  background-color: rgb(130, 130, 130);
  margin-right: 10px;
  padding-top: 15px;
  padding-bottom: 3px;
}
.tab_btn:hover {
  background-color: rgb(240, 240, 240);
  transform: scale3d(1.1, 1.1 , 1.1);
  color: black;
}
.btn1 {
  background-color: rgb(212, 212, 212);
  font-weight: bold;
  color: black;
  text-decoration: underline;
}
.main_avatar {
  margin-top: 20px;
  display: inline-block;
  width:20%;
  height: 120px;
}
.avatar_img {
  width: 40px;
}
.cu_user_in {
  width: 80px;
  background-color: rgb(30, 30, 30);
  border: none;
  font-size: 15px;
  color: white;
  margin-left: 40px;
}
.logout_div {
  display: none;
}
.logout_btn {
  margin-top: 3px;
  padding: 8px;
  border: none;
  border-radius: 5px;
  background-color: white;
  color: black;
  font-size: 15px;
}
.main_avatar:hover .logout_div {
  display: block;
}
</style>