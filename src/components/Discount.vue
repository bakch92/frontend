<template>
  <div class="discount">
    <a>지금 결제하면 {{salePrice}}% 할인</a>
  </div>

</template>

<script>
export default {
  name: 'Discount',
  data() {
    return {
      salePrice : 30
    }
  },
  mounted() {
    setInterval(()=> {
      if(this.salePrice == 0) {
        return
      } else {
        this.salePrice--;
      }
    },1000);
  },
}
</script>

<style>
.discount {
  text-align: center;
  background: #eee;
  padding: 20px;
  border-radius: 10px;
  margin-left: 20px;
  margin-right: 20px;
}
</style>