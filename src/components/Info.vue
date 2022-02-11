<template>
  <div class="info">
    <div class="img_div"><img :src="data.image" class="room_img"></div>
    <a @click="$emit('open_modal_window',data.id);">{{ data.title }}</a>
    <p>{{ data.price }} 원</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name : 'Info',
    }
  },
  props: {
    info_data : Object,
    data : Object,
  }

}
</script>

<style>

</style>