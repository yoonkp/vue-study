<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>{{ data[selectedMovie].title }}</h3>
      <p>영화 상세정보</p>
      <button @:click="$emit('closeModal')">닫기</button>
      <!-- 
        $emit('closeModal')을 통해 부모 컴포넌트에 이벤트를 전달합니다.
      -->
    </div>
  </div>
</template>
<script>
export default {
  name: "ModalComponent",
  // props로 data, isModal, selectedMovie을 받습니다.
  // props 타입은 Array, Boolean, Number입니다.
  props: {
    data: Array,
    isModal: Boolean,
    selectedMovie: Number,
  },
};
</script>
<style></style>
