<template>
  <div class="black-bg" v-if="is_modal_open == true">
    <div class="white-bg">
      <Discount/>
      <img :src="oneroom[id].image" width="100%"/>
      <h4>{{ oneroom[id].title }}</h4>
      <p>{{ oneroom[id].content }}</p>
      <input v-model="month">
      <p>{{ month }} 개월 선택함: {{ month * oneroom[id].price }}원</p>
      <button v-on:click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
import Discount from './Discount.vue'

export default {
  name: 'Modal',
  data() {
    return {
      month: 1,
    }
  },
  watch: {
    month(a) {
        if (isNaN(a) == true) {
            alert("숫자를 입력해주세요");
            this.month = 1;
        }
        else if (a >= 13) {
            alert("13 미만의 숫자를 입력해주세요");
            this.month = 1;
        }
    },
  },
  props: {
    oneroom: Array,
    id: Number,
    is_modal_open: Boolean,
  },
  components: {
    Discount: Discount,
  },
  updated() {
    if (this.month == 2) {
      alert("2개월은 너무 적음. 3개월부터 판매합니다.");
      this.month = 3;
    }
  }
}
</script>

<style>

</style>