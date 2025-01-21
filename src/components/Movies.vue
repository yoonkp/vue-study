<template>
  <div class="container">
    <h1>영화정보</h1>
    <div v-for="movie in data" :key="movie.id" class="movie">
      <figure>
        <img :src="`${movie.img}`" :alt="movie.title" height="300px" />
      </figure>
      <div class="info">
        <h3 class="bg-yellow" :style="textRed">{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button @:click="$emit('addLike', movie.id)">좋아요</button><span>{{ movie.like }}</span>
        <div>
          <button @:click="$emit('openModal', movie.id)">상세보기</button>
          <!-- $emit('openModal', i)을 통해 부모 컴포넌트에 이벤트를 전달합니다. -->
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "MoviesComponent",
  props: {
    data: Array,
    isModal: Boolean,
    selectedMovie: Number,
  },
};
</script>
<style>
.container {
  display: flex;
  flex-wrap: wrap;
  padding: 20px;
}
</style>
