<template>
  <div id ="app">
    <div class="menu">
      <a v-for="(menu,index) in menu_list" :key="index">{{menu}}</a> <!-- v-for문 이용하여 Array 형식의 menu_list 데이터 가져와서 menu 데이터 출력 -->
  </div>
    <Discount></Discount> <!-- 별도의 Discount 컴포넌트를 생성하여 해당 컴포넌트를 import 시킴 -->

    <div class="info_open_out" v-if="info_win_open == true">
      <div class="info_open_in">
        <div class="img_div"><img class="modal_image" :src="info_data[click_data].image"></div>
        <h4>{{ info_data[click_data].title }}</h4>
        <a>{{info_data[click_data].content}}</a>
        <p>가격 : {{info_data[click_data].price}}</p>
        <button @click="info_win_open = false">닫기</button>
      </div>
    </div>




    <div class="info" v-for="(data,index) in info_data" :key="index">
      <div class="img_div"><img :src="data.image" class="room_img"></div>
      <a @click="info_win_open = true; click_data = index">{{ data.title }}</a>
      <p>{{ data.price }}</p>
    </div>

    <Discount></Discount>
  </div>
</template>

<script>

import Discount from "@/components/Discount";
// import Modal from "@/components/Modal";
import data from "./assets/data.js";
export default {
  name: 'App',
  data() {
    return {
      click_data : 0,
      info_win_open : false,
      menu_list : ['Home', 'Shop', 'About'],
      info_data : data,
    }
  },
  components: {
    Discount,
    // Modal,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

div {
  box-sizing: border-box;
}

.menu {
  padding: 20px;
  background: black;
  border-radius: 20px;
  text-align: center;
  margin: 20px;
}
.menu a {
  color: white;
  margin: 20px;
  font-weight: bold;
}

.info {
  margin-top: 20px;
  text-align: center;
}

.info a {
  color: #2c3e50;
  font-weight: bold;
}

.room_img {
  width: 93%;
  border-radius: 10px;
  margin-top: 10px;
}

.info_open_out {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  padding: 20px;
  position: fixed;
  border-radius: 8px;
}

.info_open_in {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding-left: 20px;
}

.img_div {
  width: 100%;
}

.img_div .modal_image {
  margin-top: 30px;
  width: 50%;
  height: 50%;
}

button {
  margin-bottom: 20px;
}

.info_open_out .info_open_in p {
  margin : 10px;
}

</style>
