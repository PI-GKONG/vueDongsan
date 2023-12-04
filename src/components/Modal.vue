<template>
  <div class="black-bg" v-if="state == true">
    <div class="white-bg">
      <Discount/>
      <img :src='onerooms[clickId].image' alt="Image" class="room-img">
      <h4>{{ onerooms[clickId].title }}</h4>
      <p>{{ onerooms[clickId].content }}</p>
      <input v-model.number="month" />
      <p> {{ month }}개월 선택함 :{{ onerooms[clickId].price * month }} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
import Discount from './Discount.vue';

  export default {
    name: 'ModalComp',
    data() {
      return {
        month : 1,
      }
    },
    watch : {
      month(a) {
        // alert(typeof(a))
        if (isNaN(a) == true) {
          alert('글자 입력 금지')
          this.month = 1
        }
      },
    },
    props: {
        onerooms: Object,
        state: Boolean,
        clickId: Number,
    },
    components: { Discount }
}
</script>