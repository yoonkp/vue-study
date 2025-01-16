<template>
  <div class="search-box">
    <input
      type="search"
      placeholder="검색어를 입력하세요"
      @change="
        inputText = $event.target.value;
        $event.target.value = '';
      "
    />
    <!--
      input 태그에 v-model을 사용하여 inputText 데이터와 양방향 바인딩합니다.
      inputText 데이터는 사용자가 입력한 검색어를 저장합니다.
      @input="inputText = $event.currentTarget.value”를 사용해도 됩니다.
      change 이벤트는 input 태그의 값이 변경될 때 발생합니다.
    -->
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>
<script>
export default {
  name: "SearchBarComponent",
  data() {
    return {
      inputText: "",
    };
  },
  props: {
    data: Array,
  },
  watch: {
    inputText(name) {
      // 입력한 영화제목이 데이터에 있는지 확인
      const findName = this.data.filter((movie) => {
        return movie.title.includes(name);
      });
      if (findName.length == 0) {
        alert("해당하는 자료가 없습니다.");
      }
    },
  },
  // watch는 데이터의 변화를 감지하여 특정 동작을 수행합니다. (hook)
};
</script>
<style>
.search-box {
  display: flex;
  justify-content: center;
  padding: 10px;
  gap: 8px;
}
.search-box input {
  padding: 5px 10px;
  width: 280px;
  height: 36px;
}
.search-box button {
  margin: 0;
  width: 80px;
}
</style>
