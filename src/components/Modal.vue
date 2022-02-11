<template>
  <div class="info_open_out" v-if="info_win_open == true">
    <div class="info_open_in">
      <div class="img_div"><img class="modal_image" :src="info_data[click_data].image"></div>
      <h4>{{ info_data[click_data].title }}</h4>
      <a>{{info_data[click_data].content}}</a>
<!--      <input :value="quantity" @input="quantity = $event.target.value">-->
      <input :value="quantity" @input="quantity = $event.target.value">
      <p>가격 : {{info_data[click_data].price * quantity}} 원</p>
      <button @click="$emit('close_window')">닫기</button>
    </div>
  </div>

</template>

<script>
export default {
  data() {
    return {
      name : 'Modal',
      quantity : 1,
    }
  },
  props: {
    click_data : Number,
    info_data : Object,
    info_win_open : Boolean,
    data : Object,
  },
  watch: {
    quantity(a) {
      if(a > 13) {
        alert('13 이하의 숫자만 입력해주세요.');
        return this.quantity = 1;
      } else if(isNaN(a) == true) {
        alert('숫자만 입력해주세요.');
        this.quantity = 1;
      }
    }
  },
  updated() {
    if(this.quantity == 2) {
      alert('2개는 팔지 않습니다.');
      this.quantity = 3;
    }
  }

}
</script>

<style>
</style>