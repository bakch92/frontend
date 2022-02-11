<template>
  <div id ="app">
    <div class="menu">
      <a v-for="(menu,index) in menu_list" :key="index">{{menu}}</a> <!-- v-for문 이용하여 Array 형식의 menu_list 데이터 가져와서 menu 데이터 출력 -->
  </div>
    <Discount></Discount> <!-- 별도의 Discount 컴포넌트를 생성하여 해당 컴포넌트를 import 시킴 -->

    <button @click="priceSort">가격정렬</button>
    <button @click="reverseSort">가격역순정렬</button>
    <button @click="priceBack">되돌리기</button>

    <Modal @close_window = "info_win_open = false" :info_data="info_data" :click_data="click_data" :info_win_open="info_win_open"></Modal>

    <Info @open_modal_window="info_win_open = true; click_data = $event" :data="data" :info_data="info_data" v-for="(data,index) in info_data" :key="index"></Info>

    <Discount></Discount>
  </div>
</template>

<script>

import Discount from "@/components/Discount";
import Modal from "@/components/Modal";
import data from "./assets/data.js";
import Info from "./components/Info";

export default {
  name: 'App',
  data() {
    return {
      click_data : 0,
      info_win_open : false,
      menu_list : ['Home', 'Shop', 'About'],
      info_data : [...data],
      info_data_origin : data
    }
  },
  components: {
    Discount,
    Modal,
    Info,
  },
  methods: {
    priceSort() {
      this.info_data.sort(function (a,b) {
        return a.price - b.price;
      });
    },
    reverseSort() {
      this.info_data.sort(function(a,b) {
        return b.price - a.price;
      })
    },
    priceBack() {
      this.info_data = [...this.info_data_origin];
    }
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

.info_open_in a {
  display: block;
}

</style>
